<template>
  <div class="section-header" :class="{ 'section-header--center': center }">
    <span v-if="label" class="section-header__label text-mono">{{ label }}</span>
    <h2 class="section-header__title">
      <slot>{{ title }}</slot>
    </h2>
    <p v-if="subtitle" class="section-header__subtitle">{{ subtitle }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: { type: String, default: '' },
  subtitle: { type: String, default: '' },
  label: { type: String, default: '' },
  center: { type: Boolean, default: false },
})
</script>

<style scoped>
.section-header {
  margin-bottom: var(--space-12);
}

.section-header--center {
  text-align: center;
}

.section-header__label {
  display: inline-block;
  font-size: var(--text-sm);
  color: var(--color-accent);
  font-weight: 500;
  margin-bottom: var(--space-3);
  letter-spacing: var(--tracking-wide);
}

.section-header__title {
  margin-bottom: var(--space-4);
  font-size: var(--text-3xl);
}

.section-header__subtitle {
  font-size: var(--text-lg);
  color: var(--color-text-secondary);
  max-width: 650px;
  line-height: var(--leading-relaxed);
}

.section-header--center .section-header__subtitle {
  margin: 0 auto;
}

@media (max-width: 768px) {
  .section-header {
    margin-bottom: var(--space-8);
  }
}
</style>
