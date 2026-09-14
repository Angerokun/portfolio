<template>
  <section id="github" class="section section--alt">
    <div class="container">
      <ScrollReveal>
        <SectionHeader
          label="// Open Source"
          title="GitHub Repositories"
          subtitle="Selected public repositories demonstrating engineering ability."
          :center="true"
        />
      </ScrollReveal>

      <div class="github__grid">
        <ScrollReveal
          v-for="(repo, index) in repos.repositories"
          :key="index"
          :delay="Math.min(index + 1, 3)"
        >
          <a :href="repo.url" target="_blank" rel="noopener noreferrer" class="github-card card">
            <div class="github-card__header">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"/></svg>
              <h3 class="github-card__name">{{ repo.name }}</h3>
              <svg class="github-card__external" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
            </div>
            <p class="github-card__desc">{{ repo.description }}</p>
            <div class="github-card__tech">
              <span v-for="tech in repo.technologies" :key="tech" class="github-card__tech-tag">{{ tech }}</span>
            </div>
            <p v-if="repo.isPlaceholder" class="github-card__placeholder">
              ⚠ Placeholder — Replace with actual repository
            </p>
          </a>
        </ScrollReveal>
      </div>

      <ScrollReveal :delay="2">
        <div class="github__more">
          <a :href="personal.github" target="_blank" rel="noopener noreferrer" class="btn btn--secondary">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
            View All Repositories
          </a>
        </div>
      </ScrollReveal>
    </div>
  </section>
</template>

<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import ScrollReveal from '../ui/ScrollReveal.vue'
import repos from '../../data/github.json'
import personal from '../../data/personal.json'
</script>

<style scoped>
.github__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-6);
}

.github-card {
  display: flex;
  flex-direction: column;
  gap: var(--space-4);
  text-decoration: none;
  color: inherit;
}

.github-card:hover {
  color: inherit;
}

.github-card__header {
  display: flex;
  align-items: center;
  gap: var(--space-3);
  color: var(--color-accent);
}

.github-card__name {
  font-size: var(--text-base);
  font-weight: 600;
  font-family: var(--font-mono);
  color: var(--color-text-primary);
}

.github-card__external {
  margin-left: auto;
  color: var(--color-text-tertiary);
  opacity: 0;
  transition: opacity var(--transition-fast);
}

.github-card:hover .github-card__external {
  opacity: 1;
}

.github-card__desc {
  font-size: var(--text-sm);
  color: var(--color-text-secondary);
  line-height: var(--leading-relaxed);
  flex: 1;
}

.github-card__tech {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-2);
}

.github-card__tech-tag {
  font-size: var(--text-xs);
  color: var(--color-text-tertiary);
  font-family: var(--font-mono);
}

.github-card__tech-tag::before {
  content: '●';
  margin-right: var(--space-1);
  color: var(--color-accent);
  font-size: 8px;
}

.github-card__placeholder {
  font-size: var(--text-xs);
  color: var(--color-warning);
  background: rgba(245, 158, 11, 0.1);
  padding: var(--space-1) var(--space-2);
  border-radius: var(--radius-sm);
  border: 1px dashed rgba(245, 158, 11, 0.3);
}

.github__more {
  text-align: center;
  margin-top: var(--space-10);
}

@media (max-width: 768px) {
  .github__grid {
    grid-template-columns: 1fr;
  }
}
</style>
