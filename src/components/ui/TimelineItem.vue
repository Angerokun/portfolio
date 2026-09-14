<template>
  <div class="timeline-item" :class="{ 'timeline-item--placeholder': position.isPlaceholder }">
    <div class="timeline-item__marker">
      <div class="timeline-item__dot"></div>
      <div class="timeline-item__line"></div>
    </div>
    <div class="timeline-item__content card">
      <div class="timeline-item__header">
        <div>
          <h3 class="timeline-item__role">{{ position.position }}</h3>
          <p class="timeline-item__company">{{ position.company }}</p>
        </div>
        <span class="timeline-item__period text-mono">{{ position.period }}</span>
      </div>
      <ul class="timeline-item__responsibilities">
        <li v-for="(resp, i) in position.responsibilities" :key="i">{{ resp }}</li>
      </ul>
      <div class="timeline-item__tech">
        <span v-for="tech in position.technologies" :key="tech" class="tag">{{ tech }}</span>
      </div>
      <div v-if="position.achievements && position.achievements.length" class="timeline-item__achievements">
        <h4 class="timeline-item__achievements-title">Key Achievements</h4>
        <ul>
          <li v-for="(ach, i) in position.achievements" :key="i">{{ ach }}</li>
        </ul>
      </div>
      <p v-if="position.isPlaceholder" class="timeline-item__placeholder-note">
        ⚠ Placeholder entry — Replace with actual work experience before publishing
      </p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  position: { type: Object, required: true },
})
</script>

<style scoped>
.timeline-item {
  display: flex;
  gap: var(--space-6);
  position: relative;
}

.timeline-item__marker {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-shrink: 0;
  padding-top: var(--space-8);
}

.timeline-item__dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: var(--color-accent);
  box-shadow: 0 0 0 4px var(--color-accent-glow);
  z-index: 1;
  flex-shrink: 0;
}

.timeline-item__line {
  width: 2px;
  flex: 1;
  background: var(--color-border);
  margin-top: var(--space-2);
}

.timeline-item:last-child .timeline-item__line {
  display: none;
}

.timeline-item__content {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: var(--space-4);
}

.timeline-item__header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: var(--space-4);
  flex-wrap: wrap;
}

.timeline-item__role {
  font-size: var(--text-lg);
  font-weight: 700;
}

.timeline-item__company {
  font-size: var(--text-sm);
  color: var(--color-accent);
  font-weight: 500;
  margin-top: var(--space-1);
}

.timeline-item__period {
  font-size: var(--text-xs);
  color: var(--color-text-tertiary);
  white-space: nowrap;
  background: var(--color-bg-tertiary);
  padding: var(--space-1) var(--space-3);
  border-radius: var(--radius-sm);
}

.timeline-item__responsibilities {
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
}

.timeline-item__responsibilities li {
  font-size: var(--text-sm);
  color: var(--color-text-secondary);
  padding-left: var(--space-4);
  position: relative;
  line-height: var(--leading-relaxed);
}

.timeline-item__responsibilities li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: var(--color-accent);
}

.timeline-item__tech {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-2);
}

.timeline-item__achievements-title {
  font-size: var(--text-sm);
  font-weight: 600;
  margin-bottom: var(--space-2);
  color: var(--color-text-primary);
}

.timeline-item__achievements ul {
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
}

.timeline-item__achievements li {
  font-size: var(--text-sm);
  color: var(--color-text-secondary);
  padding-left: var(--space-4);
  position: relative;
}

.timeline-item__achievements li::before {
  content: '★';
  position: absolute;
  left: 0;
  color: var(--color-warning);
  font-size: var(--text-xs);
}

.timeline-item__placeholder-note {
  font-size: var(--text-xs);
  color: var(--color-warning);
  background: rgba(245, 158, 11, 0.1);
  padding: var(--space-2) var(--space-3);
  border-radius: var(--radius-sm);
  border: 1px dashed rgba(245, 158, 11, 0.3);
}

@media (max-width: 768px) {
  .timeline-item__marker {
    display: none;
  }

  .timeline-item__header {
    flex-direction: column;
  }
}
</style>
