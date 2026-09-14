<template>
  <section id="about" class="section section--alt">
    <div class="container">
      <ScrollReveal>
        <SectionHeader
          label="// About Me"
          title="Software Engineer with a Systems Mindset"
          :center="false"
        />
      </ScrollReveal>

      <div class="about__grid">
        <ScrollReveal :delay="1">
          <div class="about__text">
            <p>
              I'm a Senior Software Engineer specializing in full-stack web application development
              with a focus on building complete business systems — not just frontend interfaces.
              My work spans the entire software lifecycle: from understanding business requirements
              and designing system architecture, to writing production code, integrating hardware,
              and deploying to cloud infrastructure.
            </p>
            <p>
              I've designed and developed platforms used by real organizations —
              queue management systems for service centers, multi-tenant management platforms
              for local government units, and automation solutions that reduce manual workload.
              These aren't template projects — they're production systems handling real
              transactions, real documents, and real users.
            </p>
            <p>
              My technical foundation is built on <strong>Laravel</strong> and <strong>Vue.js</strong>,
              backed by <strong>PostgreSQL</strong> and deployed on <strong>AWS</strong> with
              <strong>Docker</strong>. But what sets my work apart is the ability to bridge
              software and hardware — integrating thermal printers, display controllers, and
              Windows-based agents into web-driven systems.
            </p>
            <p>
              I write software that solves operational problems. Whether it's a business looking
              to digitize their workflow, a government office modernizing citizen services, or a
              company wanting to automate repetitive processes — I design solutions that fit
              how organizations actually work, not the other way around.
            </p>
          </div>
        </ScrollReveal>

        <ScrollReveal :delay="2">
          <div class="about__highlights">
            <div class="about__highlight-card">
              <div class="about__highlight-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
              </div>
              <h4>Full-Stack Systems</h4>
              <p>End-to-end development from database design to cloud deployment</p>
            </div>
            <div class="about__highlight-card">
              <div class="about__highlight-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="2"/><path d="M16.24 7.76a6 6 0 0 1 0 8.49"/><path d="M7.76 16.24a6 6 0 0 1 0-8.49"/><path d="M19.07 4.93a10 10 0 0 1 0 14.14"/><path d="M4.93 19.07a10 10 0 0 1 0-14.14"/></svg>
              </div>
              <h4>Real-time Applications</h4>
              <p>WebSocket-powered systems with live updates across multiple clients</p>
            </div>
            <div class="about__highlight-card">
              <div class="about__highlight-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="4" y="4" width="16" height="16" rx="2" ry="2"/><rect x="9" y="9" width="6" height="6"/><line x1="9" y1="1" x2="9" y2="4"/><line x1="15" y1="1" x2="15" y2="4"/><line x1="9" y1="20" x2="9" y2="23"/><line x1="15" y1="20" x2="15" y2="23"/><line x1="20" y1="9" x2="23" y2="9"/><line x1="20" y1="14" x2="23" y2="14"/><line x1="1" y1="9" x2="4" y2="9"/><line x1="1" y1="14" x2="4" y2="14"/></svg>
              </div>
              <h4>Hardware Integration</h4>
              <p>Bridging web applications with physical devices and controllers</p>
            </div>
            <div class="about__highlight-card">
              <div class="about__highlight-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"/></svg>
              </div>
              <h4>Cloud & DevOps</h4>
              <p>AWS deployment with Docker, ECS, and infrastructure automation</p>
            </div>
          </div>
        </ScrollReveal>
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import ScrollReveal from '../ui/ScrollReveal.vue'
</script>

<style scoped>
.about__grid {
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: var(--space-12);
  align-items: start;
}

.about__text {
  display: flex;
  flex-direction: column;
  gap: var(--space-5);
}

.about__text p {
  font-size: var(--text-base);
  line-height: var(--leading-relaxed);
}

.about__text strong {
  color: var(--color-accent);
  font-weight: 600;
}

.about__highlights {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--space-4);
}

.about__highlight-card {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  padding: var(--space-5);
  display: flex;
  flex-direction: column;
  gap: var(--space-3);
  transition: all var(--transition-base);
}

.about__highlight-card:hover {
  border-color: var(--color-border-accent);
  background: var(--color-bg-card-hover);
}

.about__highlight-icon {
  color: var(--color-accent);
}

.about__highlight-card h4 {
  font-size: var(--text-sm);
  font-weight: 600;
}

.about__highlight-card p {
  font-size: var(--text-xs);
  color: var(--color-text-tertiary);
  line-height: var(--leading-normal);
}

@media (max-width: 1024px) {
  .about__grid {
    grid-template-columns: 1fr;
    gap: var(--space-8);
  }
}

@media (max-width: 480px) {
  .about__highlights {
    grid-template-columns: 1fr;
  }
}
</style>
