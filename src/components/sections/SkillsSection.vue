<template>
  <section id="skills" class="section">
    <div class="container">
      <ScrollReveal>
        <SectionHeader
          label="// Technical Skills"
          title="Technologies & Tools"
          subtitle="Organized by domain — the tools I use to build complete systems from frontend to infrastructure."
          :center="true"
        />
      </ScrollReveal>

      <div class="skills__grid">
        <ScrollReveal
          v-for="(category, index) in skills.categories"
          :key="category.name"
          :delay="Math.min(index + 1, 5)"
        >
          <SkillGroup :category="category" />
        </ScrollReveal>
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import ScrollReveal from '../ui/ScrollReveal.vue'
import SkillGroup from '../ui/SkillGroup.vue'
import skills from '../../data/skills.json'
</script>

<style scoped>
.skills__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-6);
}

@media (max-width: 1024px) {
  .skills__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .skills__grid {
    grid-template-columns: 1fr;
  }
}
</style>
