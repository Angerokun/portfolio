<template>
  <section id="experience" class="section section--alt">
    <div class="container container--narrow">
      <ScrollReveal>
        <SectionHeader
          label="// Work Experience"
          title="Professional Journey"
          subtitle="My career building production software systems for businesses and organizations."
        />
      </ScrollReveal>

      <div class="experience__timeline">
        <ScrollReveal
          v-for="(position, index) in experience.positions"
          :key="index"
          :delay="Math.min(index + 1, 3)"
        >
          <TimelineItem :position="position" />
        </ScrollReveal>
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import ScrollReveal from '../ui/ScrollReveal.vue'
import TimelineItem from '../ui/TimelineItem.vue'
import experience from '../../data/experience.json'
</script>

<style scoped>
.experience__timeline {
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
}
</style>
