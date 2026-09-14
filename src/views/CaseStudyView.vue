<template>
  <div class="case-study-view">
    <!-- Header / Hero Section -->
    <div class="case-study__hero">
      <div class="container">
        <router-link to="/#projects" class="back-link">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <line x1="19" y1="12" x2="5" y2="12"></line>
            <polyline points="12 19 5 12 12 5"></polyline>
          </svg>
          Back to Projects
        </router-link>

        <div v-if="project" class="case-study__header">
          <span class="badge">{{ project.category }}</span>
          <h1 class="case-study__title">{{ project.title }}</h1>
          <p class="case-study__subtitle">{{ project.subtitle }}</p>

          <div class="case-study__tech-list">
            <span v-for="tech in project.techStack" :key="tech" class="tech-tag">
              {{ tech }}
            </span>
          </div>
        </div>

        <div v-else class="case-study__not-found">
          <h2>Project Not Found</h2>
          <p>The requested case study could not be found.</p>
          <router-link to="/" class="btn btn--primary">Return Home</router-link>
        </div>
      </div>
    </div>

    <!-- Main Content -->
    <div v-if="project" class="case-study__content container">
      <!-- Overview Section -->
      <section class="cs-section">
        <div class="cs-grid">
          <div class="cs-main">
            <h2 class="cs-heading">// Executive Summary</h2>
            <p class="cs-lead">{{ project.description }}</p>

            <!-- Problem -->
            <div class="cs-block cs-block--problem">
              <h3 class="cs-subheading">
                <span class="icon">⚠️</span> The Challenge & Business Problem
              </h3>
              <p>{{ project.caseStudy.problem }}</p>
            </div>

            <!-- Requirements -->
            <div class="cs-block">
              <h3 class="cs-subheading">🎯 Key System Requirements</h3>
              <ul class="cs-list">
                <li v-for="(req, idx) in project.caseStudy.requirements" :key="idx">
                  {{ req }}
                </li>
              </ul>
            </div>

            <!-- Solution -->
            <div class="cs-block cs-block--solution">
              <h3 class="cs-subheading">
                <span class="icon">💡</span> The Solution
              </h3>
              <p>{{ project.caseStudy.solution }}</p>
            </div>

            <!-- Architecture -->
            <div class="cs-block">
              <h3 class="cs-subheading">🏛️ System Architecture</h3>
              <p>{{ project.caseStudy.architecture }}</p>

              <!-- Architecture Diagram Nodes -->
              <div v-if="project.caseStudy.architectureDiagram" class="arch-diagram">
                <h4 class="arch-diagram__title">Architecture Component Topology</h4>
                <div class="arch-nodes">
                  <div 
                    v-for="(node, idx) in project.caseStudy.architectureDiagram" 
                    :key="idx"
                    class="arch-node"
                    :class="'arch-node--' + node.type"
                  >
                    <span class="arch-node__type">{{ node.type }}</span>
                    <span class="arch-node__label">{{ node.label }}</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- Implementation Highlights -->
            <div class="cs-block">
              <h3 class="cs-subheading">⚙️ Key Implementation Highlights</h3>
              <ul class="cs-list cs-list--check">
                <li v-for="(item, idx) in project.caseStudy.implementation" :key="idx">
                  {{ item }}
                </li>
              </ul>
            </div>

            <!-- Challenges & Solutions -->
            <div class="cs-block">
              <h3 class="cs-subheading">🛠️ Technical Challenges & Solutions</h3>
              <div class="challenges-grid">
                <div 
                  v-for="(challenge, idx) in project.caseStudy.challenges" 
                  :key="idx" 
                  class="challenge-card"
                >
                  <span class="challenge-num">0{{ idx + 1 }}</span>
                  <p>{{ challenge }}</p>
                </div>
              </div>
            </div>

            <!-- Results -->
            <div class="cs-block cs-block--result">
              <h3 class="cs-subheading">
                <span class="icon">📈</span> Results & Business Impact
              </h3>
              <p class="cs-result-text">{{ project.caseStudy.result }}</p>
            </div>
          </div>

          <!-- Sidebar -->
          <aside class="cs-sidebar">
            <div class="sidebar-card">
              <h4>Project Details</h4>
              <div class="detail-item">
                <span class="detail-label">Category</span>
                <span class="detail-value">{{ project.category }}</span>
              </div>
              <div class="detail-item">
                <span class="detail-label">Role</span>
                <span class="detail-value">Lead / Full-Stack Engineer</span>
              </div>
              <div class="detail-item">
                <span class="detail-label">Technologies</span>
                <div class="tech-chips">
                  <span v-for="t in project.techStack" :key="t" class="chip">{{ t }}</span>
                </div>
              </div>
            </div>

            <div class="sidebar-card sidebar-card--cta">
              <h4>Need a similar solution?</h4>
              <p>Let's discuss how we can build custom software tailored to your operational needs.</p>
              <router-link to="/#contact" class="btn btn--primary btn--full">
                Get in Touch
              </router-link>
            </div>
          </aside>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import { computed, watchEffect } from 'vue'
import { useRoute } from 'vue-router'
import projectsData from '../data/projects.json'

const route = useRoute()

const project = computed(() => {
  const slug = route.params.slug
  return projectsData.projects.find(p => p.slug === slug)
})

watchEffect(() => {
  if (project.value) {
    document.title = `${project.value.title} — Case Study | Angelo Zamora`
  } else {
    document.title = 'Case Study | Angelo Zamora'
  }
})
</script>

<style scoped>
.case-study-view {
  min-height: 100vh;
  padding-bottom: var(--space-16);
}

.case-study__hero {
  background: linear-gradient(180deg, var(--color-bg-alt) 0%, var(--color-bg-base) 100%);
  border-bottom: 1px solid var(--color-border-subtle);
  padding: var(--space-12) 0 var(--space-10);
}

.back-link {
  display: inline-flex;
  align-items: center;
  gap: var(--space-2);
  color: var(--color-accent-teal);
  font-family: var(--font-mono);
  font-size: var(--font-size-sm);
  text-decoration: none;
  margin-bottom: var(--space-6);
  transition: transform var(--transition-fast);
}

.back-link:hover {
  transform: translateX(-4px);
}

.badge {
  display: inline-block;
  padding: var(--space-1) var(--space-3);
  background: rgba(16, 185, 129, 0.1);
  color: var(--color-accent-emerald);
  border: 1px solid rgba(16, 185, 129, 0.2);
  border-radius: var(--radius-full);
  font-family: var(--font-mono);
  font-size: var(--font-size-xs);
  margin-bottom: var(--space-3);
}

.case-study__title {
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 800;
  color: var(--color-text-bright);
  margin-bottom: var(--space-3);
  line-height: 1.2;
}

.case-study__subtitle {
  font-size: var(--font-size-lg);
  color: var(--color-text-muted);
  max-width: 800px;
  margin-bottom: var(--space-6);
}

.case-study__tech-list {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-2);
}

.tech-tag {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  color: var(--color-text-secondary);
  font-family: var(--font-mono);
  font-size: var(--font-size-xs);
  padding: var(--space-1) var(--space-3);
  border-radius: var(--radius-md);
}

.case-study__content {
  padding-top: var(--space-10);
}

.cs-grid {
  display: grid;
  grid-template-columns: 1fr 340px;
  gap: var(--space-10);
}

@media (max-width: 992px) {
  .cs-grid {
    grid-template-columns: 1fr;
  }
}

.cs-heading {
  font-family: var(--font-mono);
  color: var(--color-accent-teal);
  font-size: var(--font-size-xl);
  margin-bottom: var(--space-4);
}

.cs-lead {
  font-size: var(--font-size-lg);
  color: var(--color-text-secondary);
  line-height: 1.7;
  margin-bottom: var(--space-8);
}

.cs-block {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--space-6);
  margin-bottom: var(--space-6);
}

.cs-block--problem {
  border-left: 4px solid #f59e0b;
}

.cs-block--solution {
  border-left: 4px solid var(--color-accent-teal);
}

.cs-block--result {
  border-left: 4px solid var(--color-accent-emerald);
  background: linear-gradient(135deg, var(--color-surface) 0%, rgba(16, 185, 129, 0.05) 100%);
}

.cs-subheading {
  font-size: var(--font-size-xl);
  color: var(--color-text-bright);
  margin-bottom: var(--space-4);
  display: flex;
  align-items: center;
  gap: var(--space-2);
}

.cs-block p {
  color: var(--color-text-secondary);
  line-height: 1.7;
}

.cs-list {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: var(--space-3);
}

.cs-list li {
  position: relative;
  padding-left: var(--space-6);
  color: var(--color-text-secondary);
  line-height: 1.6;
}

.cs-list li::before {
  content: "•";
  position: absolute;
  left: var(--space-2);
  color: var(--color-accent-teal);
  font-weight: bold;
}

.cs-list--check li::before {
  content: "✓";
  color: var(--color-accent-emerald);
}

.arch-diagram {
  margin-top: var(--space-6);
  padding-top: var(--space-4);
  border-top: 1px dashed var(--color-border);
}

.arch-diagram__title {
  font-family: var(--font-mono);
  font-size: var(--font-size-sm);
  color: var(--color-text-muted);
  margin-bottom: var(--space-4);
}

.arch-nodes {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-3);
}

.arch-node {
  display: flex;
  flex-direction: column;
  padding: var(--space-2) var(--space-3);
  background: var(--color-bg-base);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
}

.arch-node__type {
  font-family: var(--font-mono);
  font-size: 10px;
  text-transform: uppercase;
  color: var(--color-text-muted);
  letter-spacing: 0.05em;
}

.arch-node__label {
  font-size: var(--font-size-sm);
  color: var(--color-text-bright);
  font-weight: 500;
}

.challenges-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-4);
}

.challenge-card {
  display: flex;
  gap: var(--space-4);
  background: var(--color-bg-base);
  padding: var(--space-4);
  border-radius: var(--radius-md);
  border: 1px solid var(--color-border-subtle);
}

.challenge-num {
  font-family: var(--font-mono);
  font-weight: 700;
  color: var(--color-accent-teal);
  font-size: var(--font-size-lg);
}

.cs-sidebar {
  display: flex;
  flex-direction: column;
  gap: var(--space-6);
}

.sidebar-card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--space-6);
}

.sidebar-card h4 {
  font-size: var(--font-size-md);
  color: var(--color-text-bright);
  margin-bottom: var(--space-4);
  border-bottom: 1px solid var(--color-border);
  padding-bottom: var(--space-2);
}

.detail-item {
  margin-bottom: var(--space-4);
}

.detail-label {
  display: block;
  font-size: var(--font-size-xs);
  font-family: var(--font-mono);
  color: var(--color-text-muted);
  margin-bottom: var(--space-1);
}

.detail-value {
  color: var(--color-text-primary);
  font-size: var(--font-size-sm);
}

.tech-chips {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-1);
  margin-top: var(--space-2);
}

.chip {
  background: var(--color-bg-base);
  border: 1px solid var(--color-border-subtle);
  padding: 2px 8px;
  border-radius: var(--radius-sm);
  font-size: var(--font-size-xs);
  font-family: var(--font-mono);
  color: var(--color-text-muted);
}

.sidebar-card--cta {
  background: linear-gradient(135deg, rgba(20, 184, 166, 0.1) 0%, var(--color-surface) 100%);
  border-color: rgba(20, 184, 166, 0.3);
}

.btn--full {
  width: 100%;
  text-align: center;
  justify-content: center;
  margin-top: var(--space-4);
}

.case-study__not-found {
  padding: var(--space-12) 0;
  text-align: center;
}
</style>
