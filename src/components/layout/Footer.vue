<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__top">
        <div class="footer__brand">
          <span class="footer__logo text-mono">
            <span class="text-accent">&lt;</span>AZ<span class="text-accent"> /&gt;</span>
          </span>
          <p class="footer__tagline">Senior Software Engineer & Full-Stack Developer</p>
        </div>
        <div class="footer__links">
          <h4 class="footer__heading">Navigation</h4>
          <a href="#about" @click="handleNavClick($event, '#about')">About</a>
          <a href="#skills" @click="handleNavClick($event, '#skills')">Skills</a>
          <a href="#projects" @click="handleNavClick($event, '#projects')">Projects</a>
          <a href="#services" @click="handleNavClick($event, '#services')">Services</a>
          <a href="#contact" @click="handleNavClick($event, '#contact')">Contact</a>
        </div>
        <div class="footer__links">
          <h4 class="footer__heading">Connect</h4>
          <a :href="personal.github" target="_blank" rel="noopener noreferrer">GitHub</a>
          <a :href="personal.linkedin" target="_blank" rel="noopener noreferrer">LinkedIn</a>
          <a :href="'mailto:' + personal.email">Email</a>
        </div>
      </div>
      <div class="footer__bottom">
        <p class="footer__copyright">
          &copy; {{ currentYear }} Angelo Zamora. All rights reserved.
        </p>
        <p class="footer__credit">
          Built with Vue.js & deployed with care.
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { useRouter, useRoute } from 'vue-router'
import personal from '../../data/personal.json'

const router = useRouter()
const route = useRoute()
const currentYear = new Date().getFullYear()

function handleNavClick(event, href) {
  event.preventDefault()
  if (route.name !== 'Home') {
    router.push('/').then(() => {
      setTimeout(() => {
        const el = document.getElementById(href.replace('#', ''))
        if (el) {
          const navHeight = 70
          const elementPosition = el.getBoundingClientRect().top + window.pageYOffset
          window.scrollTo({ top: elementPosition - navHeight, behavior: 'smooth' })
        }
      }, 100)
    })
  } else {
    const el = document.getElementById(href.replace('#', ''))
    if (el) {
      const navHeight = 70
      const elementPosition = el.getBoundingClientRect().top + window.pageYOffset
      window.scrollTo({ top: elementPosition - navHeight, behavior: 'smooth' })
    }
  }
}
</script>

<style scoped>
.footer {
  background: var(--color-bg-secondary);
  border-top: 1px solid var(--color-border);
  padding: var(--space-16) 0 var(--space-8);
}

.footer__top {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: var(--space-12);
  padding-bottom: var(--space-12);
  border-bottom: 1px solid var(--color-border);
}

.footer__brand {
  display: flex;
  flex-direction: column;
  gap: var(--space-3);
}

.footer__logo {
  font-size: var(--text-xl);
  font-weight: 600;
  color: var(--color-text-primary);
}

.footer__tagline {
  font-size: var(--text-sm);
  color: var(--color-text-tertiary);
  max-width: 300px;
}

.footer__heading {
  font-size: var(--text-sm);
  font-weight: 600;
  color: var(--color-text-primary);
  margin-bottom: var(--space-4);
  text-transform: uppercase;
  letter-spacing: var(--tracking-wide);
}

.footer__links {
  display: flex;
  flex-direction: column;
  gap: var(--space-3);
}

.footer__links a {
  color: var(--color-text-tertiary);
  font-size: var(--text-sm);
  transition: color var(--transition-fast);
  text-decoration: none;
}

.footer__links a:hover {
  color: var(--color-accent);
}

.footer__bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: var(--space-8);
}

.footer__copyright {
  font-size: var(--text-sm);
  color: var(--color-text-tertiary);
}

.footer__credit {
  font-size: var(--text-xs);
  color: var(--color-text-tertiary);
}

@media (max-width: 768px) {
  .footer__top {
    grid-template-columns: 1fr;
    gap: var(--space-8);
  }

  .footer__bottom {
    flex-direction: column;
    gap: var(--space-3);
    text-align: center;
  }
}
</style>
