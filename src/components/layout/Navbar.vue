<template>
  <nav class="navbar" :class="{ 'navbar--scrolled': isScrolled, 'navbar--open': isMobileOpen }">
    <div class="container navbar__container">
      <router-link to="/" class="navbar__logo" @click="handleLogoClick">
        <span class="navbar__logo-bracket">&lt;</span>
        <span class="navbar__logo-name">AZ</span>
        <span class="navbar__logo-bracket"> /&gt;</span>
      </router-link>

      <div class="navbar__links" :class="{ 'navbar__links--open': isMobileOpen }">
        <a
          v-for="link in navLinks"
          :key="link.id"
          :href="link.href"
          class="navbar__link"
          @click="handleNavClick($event, link)"
        >
          {{ link.label }}
        </a>
        <a :href="personal.resumePath" target="_blank" class="btn btn--secondary navbar__resume-btn">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
          Resume
        </a>
      </div>

      <button
        class="navbar__toggle"
        :class="{ 'navbar__toggle--open': isMobileOpen }"
        @click="toggleMobile"
        aria-label="Toggle navigation menu"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useRouter, useRoute } from 'vue-router'
import personal from '../../data/personal.json'

const router = useRouter()
const route = useRoute()
const isScrolled = ref(false)
const isMobileOpen = ref(false)

const navLinks = [
  { id: 'about', label: 'About', href: '#about' },
  { id: 'skills', label: 'Skills', href: '#skills' },
  { id: 'projects', label: 'Projects', href: '#projects' },
  { id: 'services', label: 'Services', href: '#services' },
  { id: 'experience', label: 'Experience', href: '#experience' },
  { id: 'contact', label: 'Contact', href: '#contact' },
]

function handleScroll() {
  isScrolled.value = window.scrollY > 50
}

function toggleMobile() {
  isMobileOpen.value = !isMobileOpen.value
  document.body.style.overflow = isMobileOpen.value ? 'hidden' : ''
}

function closeMobile() {
  isMobileOpen.value = false
  document.body.style.overflow = ''
}

function scrollToSection(sectionId) {
  const elementId = sectionId.replace('#', '')
  const element = document.getElementById(elementId)
  if (element) {
    const navHeight = 70
    const elementPosition = element.getBoundingClientRect().top + window.pageYOffset
    const offsetPosition = elementPosition - navHeight

    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth'
    })
  }
}

function handleLogoClick(event) {
  closeMobile()
  if (route.name === 'Home') {
    event.preventDefault()
    window.scrollTo({ top: 0, behavior: 'smooth' })
  }
}

function handleNavClick(event, link) {
  event.preventDefault()
  closeMobile()

  if (route.name !== 'Home') {
    router.push('/').then(() => {
      setTimeout(() => {
        scrollToSection(link.href)
      }, 100)
    })
  } else {
    scrollToSection(link.href)
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: var(--z-nav);
  padding: var(--space-4) 0;
  transition: all var(--transition-base);
  background: transparent;
}

.navbar--scrolled {
  background: rgba(10, 15, 26, 0.85);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--color-border);
  padding: var(--space-3) 0;
}

.navbar__container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.navbar__logo {
  font-family: var(--font-mono);
  font-size: var(--text-lg);
  font-weight: 600;
  color: var(--color-text-primary);
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 2px;
  z-index: var(--z-nav);
}

.navbar__logo:hover {
  color: var(--color-text-primary);
}

.navbar__logo-bracket {
  color: var(--color-accent);
}

.navbar__logo-name {
  color: var(--color-text-primary);
}

.navbar__links {
  display: flex;
  align-items: center;
  gap: var(--space-1);
}

.navbar__link {
  color: var(--color-text-secondary);
  font-size: var(--text-sm);
  font-weight: 500;
  padding: var(--space-2) var(--space-3);
  border-radius: var(--radius-sm);
  transition: all var(--transition-fast);
  text-decoration: none;
}

.navbar__link:hover {
  color: var(--color-accent);
  background: var(--color-accent-glow);
}

.navbar__resume-btn {
  margin-left: var(--space-3);
  font-size: var(--text-xs);
  padding: var(--space-2) var(--space-4);
}

.navbar__toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  padding: var(--space-2);
  z-index: var(--z-nav);
}

.navbar__toggle span {
  display: block;
  width: 22px;
  height: 2px;
  background: var(--color-text-primary);
  border-radius: 2px;
  transition: all var(--transition-base);
}

.navbar__toggle--open span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.navbar__toggle--open span:nth-child(2) {
  opacity: 0;
}

.navbar__toggle--open span:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* Mobile */
@media (max-width: 768px) {
  .navbar__toggle {
    display: flex;
  }

  .navbar__links {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(10, 15, 26, 0.98);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    flex-direction: column;
    justify-content: center;
    gap: var(--space-6);
    opacity: 0;
    pointer-events: none;
    transition: opacity var(--transition-base);
  }

  .navbar__links--open {
    opacity: 1;
    pointer-events: all;
  }

  .navbar__link {
    font-size: var(--text-xl);
    padding: var(--space-3) var(--space-6);
  }

  .navbar__resume-btn {
    margin-left: 0;
    margin-top: var(--space-4);
    font-size: var(--text-sm);
  }
}
</style>
