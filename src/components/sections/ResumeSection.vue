<template>
  <section id="resume" class="section">
    <div class="container container--narrow">
      <ScrollReveal>
        <SectionHeader
          label="// Resume"
          title="Download My Resume"
          subtitle="A comprehensive overview of my skills, experience, and qualifications."
          :center="true"
        />
      </ScrollReveal>

      <ScrollReveal :delay="1">
        <div class="resume__card card">
          <div class="resume__content">
            <div class="resume__icon">
              <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>
            </div>

            <div class="resume__info">
              <h3>Angelo Zamora</h3>
              <p class="resume__role">Senior Software Engineer | Full-Stack Developer</p>
              <div class="resume__summary">
                <div class="resume__summary-item">
                  <span class="resume__summary-label">Core Stack</span>
                  <span class="resume__summary-value">Laravel · Vue.js · PostgreSQL · AWS</span>
                </div>
                <div class="resume__summary-item">
                  <span class="resume__summary-label">Specialization</span>
                  <span class="resume__summary-value">Business Systems · Automation · System Integration</span>
                </div>
                <div class="resume__summary-item">
                  <span class="resume__summary-label">Deployment</span>
                  <span class="resume__summary-value">Docker · AWS ECS · Fargate · CI/CD</span>
                </div>
              </div>
            </div>
          </div>

          <a :href="personal.resumePath" target="_blank" class="btn btn--primary resume__download">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
            Download Resume (PDF)
          </a>
        </div>
      </ScrollReveal>
    </div>
  </section>
</template>

<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import ScrollReveal from '../ui/ScrollReveal.vue'
import personal from '../../data/personal.json'
</script>

<style scoped>
.resume__card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-8);
  padding: var(--space-12);
  text-align: center;
  max-width: 700px;
  margin: 0 auto;
}

.resume__card:hover {
  transform: none;
}

.resume__content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-6);
}

.resume__icon {
  color: var(--color-accent);
  opacity: 0.8;
}

.resume__info h3 {
  font-size: var(--text-2xl);
  margin-bottom: var(--space-2);
}

.resume__role {
  font-size: var(--text-sm);
  color: var(--color-accent);
  font-weight: 500;
}

.resume__summary {
  display: flex;
  flex-direction: column;
  gap: var(--space-3);
  margin-top: var(--space-6);
  width: 100%;
}

.resume__summary-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--space-3) 0;
  border-bottom: 1px solid var(--color-border);
  gap: var(--space-4);
}

.resume__summary-item:last-child {
  border-bottom: none;
}

.resume__summary-label {
  font-size: var(--text-sm);
  font-weight: 600;
  color: var(--color-text-primary);
  white-space: nowrap;
}

.resume__summary-value {
  font-size: var(--text-sm);
  color: var(--color-text-secondary);
  font-family: var(--font-mono);
  text-align: right;
}

.resume__download {
  margin-top: var(--space-2);
}

@media (max-width: 600px) {
  .resume__card {
    padding: var(--space-8);
  }

  .resume__summary-item {
    flex-direction: column;
    align-items: flex-start;
    gap: var(--space-1);
  }

  .resume__summary-value {
    text-align: left;
  }
}
</style>
