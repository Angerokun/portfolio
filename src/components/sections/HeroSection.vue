<template>
  <section id="hero" class="hero">
    <!-- Animated background -->
    <div class="hero__bg">
      <div class="hero__grid"></div>
      <div class="hero__glow hero__glow--1"></div>
      <div class="hero__glow hero__glow--2"></div>
    </div>

    <div class="container hero__container">
      <div class="hero__content">
        <span class="hero__greeting text-mono">Hi, my name is</span>
        <h1 class="hero__name">
          Angelo <span class="text-gradient">Zamora</span>
        </h1>
        <h2 class="hero__title">{{ personal.title }}</h2>
        <p class="hero__tagline">{{ personal.tagline }}</p>

        <div class="hero__actions">
          <a href="#projects" class="btn btn--primary" @click="scrollToSection($event, '#projects')">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/><path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/></svg>
            View My Work
          </a>
          <a href="#contact" class="btn btn--secondary" @click="scrollToSection($event, '#contact')">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
            Contact Me
          </a>
        </div>

        <div class="hero__social">
          <a :href="personal.github" target="_blank" rel="noopener noreferrer" class="hero__social-link" aria-label="GitHub Profile">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
          </a>
          <a :href="personal.linkedin" target="_blank" rel="noopener noreferrer" class="hero__social-link" aria-label="LinkedIn Profile">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          </a>
          <a :href="personal.resumePath" target="_blank" class="hero__social-link" aria-label="Download Resume">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>
          </a>
        </div>
      </div>

      <div class="hero__visual">
        <div class="hero__terminal">
          <div class="hero__terminal-bar">
            <span class="hero__terminal-dot hero__terminal-dot--red"></span>
            <span class="hero__terminal-dot hero__terminal-dot--yellow"></span>
            <span class="hero__terminal-dot hero__terminal-dot--green"></span>
            <span class="hero__terminal-title text-mono">terminal</span>
          </div>
          <div class="hero__terminal-body text-mono">
            <div class="hero__terminal-line">
              <span class="hero__terminal-prompt">$</span>
              <span class="hero__terminal-text">whoami</span>
            </div>
            <div class="hero__terminal-line hero__terminal-line--output">
              <span>Senior Software Engineer</span>
            </div>
            <div class="hero__terminal-line">
              <span class="hero__terminal-prompt">$</span>
              <span class="hero__terminal-text">cat specialties.txt</span>
            </div>
            <div class="hero__terminal-line hero__terminal-line--output">
              <span>Full-Stack Development</span>
            </div>
            <div class="hero__terminal-line hero__terminal-line--output">
              <span>Business Systems & Automation</span>
            </div>
            <div class="hero__terminal-line hero__terminal-line--output">
              <span>System Architecture & Deployment</span>
            </div>
            <div class="hero__terminal-line">
              <span class="hero__terminal-prompt">$</span>
              <span class="hero__terminal-text hero__terminal-cursor">_</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll indicator -->
    <div class="hero__scroll">
      <span class="text-mono text-xs">scroll</span>
      <div class="hero__scroll-line"></div>
    </div>
  </section>
</template>

<script setup>
import personal from '../../data/personal.json'

function scrollToSection(event, sectionId) {
  event.preventDefault()
  const el = document.getElementById(sectionId.replace('#', ''))
  if (el) {
    const navHeight = 70
    const elementPosition = el.getBoundingClientRect().top + window.pageYOffset
    const offsetPosition = elementPosition - navHeight
    window.scrollTo({ top: offsetPosition, behavior: 'smooth' })
  }
}
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  padding-top: var(--nav-height);
}

/* Background effects */
.hero__bg {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.hero__grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(148, 163, 184, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(148, 163, 184, 0.03) 1px, transparent 1px);
  background-size: 60px 60px;
  animation: dotPulse 8s ease-in-out infinite;
}

.hero__glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
}

.hero__glow--1 {
  width: 500px;
  height: 500px;
  background: rgba(56, 189, 169, 0.08);
  top: 10%;
  right: 10%;
  animation: float 12s ease-in-out infinite;
}

.hero__glow--2 {
  width: 400px;
  height: 400px;
  background: rgba(99, 102, 241, 0.06);
  bottom: 10%;
  left: 5%;
  animation: float 15s ease-in-out infinite reverse;
}

.hero__container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--space-16);
  align-items: center;
  padding: var(--space-16) var(--space-6);
  position: relative;
  z-index: 1;
}

.hero__content {
  display: flex;
  flex-direction: column;
  gap: var(--space-4);
  animation: fadeInUp 0.8s ease-out;
}

.hero__greeting {
  font-size: var(--text-sm);
  color: var(--color-accent);
  font-weight: 500;
}

.hero__name {
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 800;
  letter-spacing: var(--tracking-tight);
  line-height: 1.1;
}

.hero__title {
  font-size: var(--text-xl);
  color: var(--color-text-secondary);
  font-weight: 500;
  line-height: var(--leading-normal);
}

.hero__tagline {
  font-size: var(--text-lg);
  color: var(--color-text-secondary);
  max-width: 520px;
  line-height: var(--leading-relaxed);
  margin-top: var(--space-2);
}

.hero__actions {
  display: flex;
  gap: var(--space-4);
  margin-top: var(--space-6);
  flex-wrap: wrap;
}

.hero__social {
  display: flex;
  gap: var(--space-3);
  margin-top: var(--space-6);
}

.hero__social-link {
  width: 42px;
  height: 42px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--radius-md);
  color: var(--color-text-tertiary);
  border: 1px solid var(--color-border);
  transition: all var(--transition-base);
}

.hero__social-link:hover {
  color: var(--color-accent);
  border-color: var(--color-border-accent);
  background: var(--color-accent-glow);
  transform: translateY(-2px);
}

/* Terminal visual */
.hero__visual {
  display: flex;
  justify-content: center;
  align-items: center;
  animation: fadeInUp 0.8s ease-out 0.2s both;
}

.hero__terminal {
  width: 100%;
  max-width: 460px;
  border-radius: var(--radius-lg);
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  overflow: hidden;
  box-shadow: var(--shadow-xl);
}

.hero__terminal-bar {
  display: flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-3) var(--space-4);
  background: var(--color-bg-tertiary);
  border-bottom: 1px solid var(--color-border);
}

.hero__terminal-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.hero__terminal-dot--red { background: #ff5f57; }
.hero__terminal-dot--yellow { background: #febc2e; }
.hero__terminal-dot--green { background: #28c840; }

.hero__terminal-title {
  margin-left: auto;
  margin-right: auto;
  font-size: var(--text-xs);
  color: var(--color-text-tertiary);
}

.hero__terminal-body {
  padding: var(--space-6);
  display: flex;
  flex-direction: column;
  gap: var(--space-3);
}

.hero__terminal-line {
  display: flex;
  gap: var(--space-3);
  font-size: var(--text-sm);
  color: var(--color-text-primary);
}

.hero__terminal-line--output {
  color: var(--color-text-secondary);
  padding-left: calc(var(--space-3) + 0.6em);
}

.hero__terminal-prompt {
  color: var(--color-accent);
  font-weight: 600;
}

.hero__terminal-text {
  color: var(--color-text-primary);
}

.hero__terminal-cursor {
  animation: subtlePulse 1.2s ease-in-out infinite;
  color: var(--color-accent);
}

/* Scroll indicator */
.hero__scroll {
  position: absolute;
  bottom: var(--space-8);
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-2);
  color: var(--color-text-tertiary);
  animation: float 3s ease-in-out infinite;
}

.hero__scroll-line {
  width: 1px;
  height: 30px;
  background: linear-gradient(to bottom, var(--color-accent), transparent);
}

@media (max-width: 1024px) {
  .hero__container {
    grid-template-columns: 1fr;
    gap: var(--space-12);
    text-align: center;
  }

  .hero__tagline {
    margin-left: auto;
    margin-right: auto;
  }

  .hero__actions {
    justify-content: center;
  }

  .hero__social {
    justify-content: center;
  }

  .hero__visual {
    order: -1;
  }

  .hero__terminal {
    max-width: 400px;
  }
}

@media (max-width: 480px) {
  .hero__actions {
    flex-direction: column;
    align-items: stretch;
  }

  .hero__actions .btn {
    justify-content: center;
  }
}
</style>
