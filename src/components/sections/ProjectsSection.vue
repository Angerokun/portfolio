<template>
  <section id="projects" class="section section--alt">
    <div class="container">
      <ScrollReveal>
        <SectionHeader
          label="// Featured Projects"
          title="Real Systems, Real Solutions"
          subtitle="Production systems designed and built to solve actual business and operational problems."
          :center="true"
        />
      </ScrollReveal>

      <div class="projects__grid">
        <ScrollReveal
          v-for="(project, index) in featuredProjects"
          :key="project.slug"
          :delay="Math.min(index + 1, 4)"
        >
          <ProjectCard :project="project" />
        </ScrollReveal>
      </div>
    </div>
  </section>
</template>

<script setup>
import { computed } from 'vue'
import SectionHeader from '../ui/SectionHeader.vue'
import ScrollReveal from '../ui/ScrollReveal.vue'
import ProjectCard from '../ui/ProjectCard.vue'
import projectsData from '../../data/projects.json'

const featuredProjects = computed(() => {
  return projectsData.projects.filter(p => p.featured)
})
</script>

<style scoped>
.projects__grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--space-8);
}

@media (max-width: 768px) {
  .projects__grid {
    grid-template-columns: 1fr;
  }
}
</style>
