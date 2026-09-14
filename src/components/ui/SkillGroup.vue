<template>
  <div class="skill-group card">
    <div class="skill-group__header">
      <div class="skill-group__icon">
        <svg v-if="category.icon === 'layout'" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"/><line x1="3" y1="9" x2="21" y2="9"/><line x1="9" y1="21" x2="9" y2="9"/></svg>
        <svg v-else-if="category.icon === 'server'" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="8" rx="2" ry="2"/><rect x="2" y="14" width="20" height="8" rx="2" ry="2"/><line x1="6" y1="6" x2="6.01" y2="6"/><line x1="6" y1="18" x2="6.01" y2="18"/></svg>
        <svg v-else-if="category.icon === 'database'" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></svg>
        <svg v-else-if="category.icon === 'cloud'" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"/></svg>
        <svg v-else-if="category.icon === 'radio'" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16.72 11.06A10.94 10.94 0 0 1 19 12.55"/><path d="M13.02 7.34A16 16 0 0 1 22 12"/><path d="M2 12C2 6.48 6.44 2 12 2"/><path d="M5 12a7 7 0 0 1 7-7"/><circle cx="12" cy="12" r="2"/><path d="m12 14 7 8"/></svg>
        <svg v-else width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"/></svg>
      </div>
      <h3 class="skill-group__name">{{ category.name }}</h3>
    </div>
    <div class="skill-group__tags">
      <span v-for="skill in category.skills" :key="skill" class="tag">{{ skill }}</span>
    </div>
  </div>
</template>

<script setup>
defineProps({
  category: { type: Object, required: true },
})
</script>

<style scoped>
.skill-group {
  display: flex;
  flex-direction: column;
  gap: var(--space-6);
}

.skill-group__header {
  display: flex;
  align-items: center;
  gap: var(--space-3);
}

.skill-group__icon {
  width: 42px;
  height: 42px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--radius-md);
  background: var(--color-accent-glow);
  color: var(--color-accent);
  flex-shrink: 0;
}

.skill-group__name {
  font-size: var(--text-lg);
  font-weight: 600;
}

.skill-group__tags {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-2);
}
</style>
