<template>
  <div class="home-view">
    <HeroSection />
    <AboutSection />
    <SkillsSection />
    <ProjectsSection />
    <ServicesSection />
    <ExperienceSection />
    <ResumeSection />
    <GitHubSection />
    <ContactSection />
  </div>
</template>

<script setup>
import HeroSection from '../components/sections/HeroSection.vue'
import AboutSection from '../components/sections/AboutSection.vue'
import SkillsSection from '../components/sections/SkillsSection.vue'
import ProjectsSection from '../components/sections/ProjectsSection.vue'
import ServicesSection from '../components/sections/ServicesSection.vue'
import ExperienceSection from '../components/sections/ExperienceSection.vue'
import ResumeSection from '../components/sections/ResumeSection.vue'
import GitHubSection from '../components/sections/GitHubSection.vue'
import ContactSection from '../components/sections/ContactSection.vue'
</script>

<style scoped>
.home-view {
  width: 100%;
}
</style>
