<template>
  <router-link :to="`/project/${project.slug}`" class="project-card card">
    <div class="project-card__thumbnail">
      <div class="project-card__thumbnail-inner">
        <svg v-if="project.category === 'Business System'" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
        <svg v-else-if="project.category === 'Government System'" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M3 21h18"/><path d="M5 21V7l8-4v18"/><path d="M19 21V11l-6-4"/><path d="M9 9h1"/><path d="M9 13h1"/><path d="M9 17h1"/></svg>
        <svg v-else-if="project.category === 'AI & Automation'" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2a4 4 0 0 1 4 4v2a4 4 0 0 1-8 0V6a4 4 0 0 1 4-4z"/><path d="M16 14h.01"/><path d="M8 14h.01"/><path d="M12 17v3"/><path d="M7 20h10"/><circle cx="12" cy="14" r="7"/></svg>
        <svg v-else width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"/></svg>
      </div>
      <span class="project-card__category tag">{{ project.category }}</span>
    </div>
    <div class="project-card__content">
      <h3 class="project-card__title">{{ project.title }}</h3>
      <p class="project-card__desc">{{ project.description }}</p>
      <div class="project-card__tech">
        <span v-for="tech in displayTech" :key="tech" class="project-card__tech-tag">{{ tech }}</span>
        <span v-if="project.techStack.length > maxTechDisplay" class="project-card__tech-more">
          +{{ project.techStack.length - maxTechDisplay }}
        </span>
      </div>
      <span class="project-card__cta">
        View Case Study
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
      </span>
    </div>
  </router-link>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  project: { type: Object, required: true },
})

const maxTechDisplay = 5

const displayTech = computed(() => {
  return props.project.techStack.slice(0, maxTechDisplay)
})
</script>

<style scoped>
.project-card {
  display: flex;
  flex-direction: column;
  text-decoration: none;
  color: inherit;
  overflow: hidden;
  padding: 0;
}

.project-card:hover {
  color: inherit;
}

.project-card__thumbnail {
  position: relative;
  background: linear-gradient(135deg, var(--color-bg-tertiary), var(--color-bg-secondary));
  padding: var(--space-12) var(--space-8);
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 200px;
  overflow: hidden;
}

.project-card__thumbnail::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at 30% 50%, var(--color-accent-glow) 0%, transparent 70%);
  opacity: 0;
  transition: opacity var(--transition-base);
}

.project-card:hover .project-card__thumbnail::before {
  opacity: 1;
}

.project-card__thumbnail-inner {
  color: var(--color-accent);
  opacity: 0.6;
  transition: all var(--transition-base);
}

.project-card:hover .project-card__thumbnail-inner {
  opacity: 1;
  transform: scale(1.1);
}

.project-card__category {
  position: absolute;
  top: var(--space-4);
  right: var(--space-4);
}

.project-card__content {
  padding: var(--space-6) var(--space-8) var(--space-8);
  display: flex;
  flex-direction: column;
  gap: var(--space-4);
  flex: 1;
}

.project-card__title {
  font-size: var(--text-xl);
  font-weight: 700;
}

.project-card__desc {
  font-size: var(--text-sm);
  color: var(--color-text-secondary);
  line-height: var(--leading-relaxed);
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.project-card__tech {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-2);
  margin-top: auto;
}

.project-card__tech-tag {
  font-size: var(--text-xs);
  color: var(--color-text-tertiary);
  font-family: var(--font-mono);
  background: var(--color-bg-tertiary);
  padding: 2px var(--space-2);
  border-radius: var(--radius-sm);
}

.project-card__tech-more {
  font-size: var(--text-xs);
  color: var(--color-text-tertiary);
  padding: 2px var(--space-2);
}

.project-card__cta {
  display: inline-flex;
  align-items: center;
  gap: var(--space-2);
  font-size: var(--text-sm);
  font-weight: 600;
  color: var(--color-accent);
  margin-top: var(--space-2);
  transition: gap var(--transition-base);
}

.project-card:hover .project-card__cta {
  gap: var(--space-3);
}
</style>
