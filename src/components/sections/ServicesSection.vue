<template>
  <section id="services" class="section">
    <div class="container">
      <ScrollReveal>
        <SectionHeader
          label="// Services"
          title="How I Can Help Your Business"
          subtitle="I build custom software solutions tailored to how your organization actually works."
          :center="true"
        />
      </ScrollReveal>

      <div class="services__grid">
        <ScrollReveal
          v-for="(service, index) in services.services"
          :key="service.title"
          :delay="Math.min((index % 3) + 1, 3)"
        >
          <ServiceCard :service="service" />
        </ScrollReveal>
      </div>

      <ScrollReveal :delay="2">
        <div class="services__cta">
          <p>Have a project in mind? Let's discuss how I can help.</p>
          <a href="#contact" class="btn btn--primary">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
            Get In Touch
          </a>
        </div>
      </ScrollReveal>
    </div>
  </section>
</template>

<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import ScrollReveal from '../ui/ScrollReveal.vue'
import ServiceCard from '../ui/ServiceCard.vue'
import services from '../../data/services.json'
</script>

<style scoped>
.services__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-6);
}

.services__cta {
  text-align: center;
  margin-top: var(--space-12);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-6);
}

.services__cta p {
  font-size: var(--text-lg);
  color: var(--color-text-secondary);
}

@media (max-width: 1024px) {
  .services__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .services__grid {
    grid-template-columns: 1fr;
  }
}
</style>
