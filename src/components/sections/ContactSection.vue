<template>
  <section id="contact" class="section">
    <div class="container container--narrow">
      <ScrollReveal>
        <SectionHeader
          label="// Contact"
          title="Let's Work Together"
          subtitle="Whether you're a recruiter looking for an experienced engineer or a business looking for a custom software solution — I'd love to hear from you."
          :center="true"
        />
      </ScrollReveal>

      <div class="contact__grid">
        <ScrollReveal :delay="1">
          <div class="contact__info">
            <div class="contact__info-card card">
              <div class="contact__info-icon">
                <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
              </div>
              <div>
                <h4>Email</h4>
                <a :href="'mailto:' + personal.email">{{ personal.email }}</a>
              </div>
            </div>

            <div class="contact__info-card card">
              <div class="contact__info-icon">
                <svg width="22" height="22" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
              </div>
              <div>
                <h4>GitHub</h4>
                <a :href="personal.github" target="_blank" rel="noopener noreferrer">{{ personal.github.replace('https://', '') }}</a>
              </div>
            </div>

            <div class="contact__info-card card">
              <div class="contact__info-icon">
                <svg width="22" height="22" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
              </div>
              <div>
                <h4>LinkedIn</h4>
                <a :href="personal.linkedin" target="_blank" rel="noopener noreferrer">{{ personal.linkedin.replace('https://', '') }}</a>
              </div>
            </div>
          </div>
        </ScrollReveal>

        <ScrollReveal :delay="2">
          <form class="contact__form card" @submit.prevent="handleSubmit">
            <h3 class="contact__form-title">Send a Message</h3>
            <div class="contact__form-group">
              <label for="contact-name">Name</label>
              <input
                id="contact-name"
                v-model="form.name"
                type="text"
                placeholder="Your name"
                required
              />
            </div>
            <div class="contact__form-group">
              <label for="contact-email">Email</label>
              <input
                id="contact-email"
                v-model="form.email"
                type="email"
                placeholder="your@email.com"
                required
              />
            </div>
            <div class="contact__form-group">
              <label for="contact-subject">Subject</label>
              <input
                id="contact-subject"
                v-model="form.subject"
                type="text"
                placeholder="Project inquiry / Job opportunity / etc."
              />
            </div>
            <div class="contact__form-group">
              <label for="contact-message">Message</label>
              <textarea
                id="contact-message"
                v-model="form.message"
                rows="5"
                placeholder="Tell me about your project or opportunity..."
                required
              ></textarea>
            </div>
            <button type="submit" class="btn btn--primary contact__form-submit" :disabled="isSubmitting">
              <svg v-if="!isSubmitting" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
              <span v-if="isSubmitting">Sending...</span>
              <span v-else>Send Message</span>
            </button>
            <p v-if="submitStatus === 'success'" class="contact__form-status contact__form-status--success">
              ✓ Message sent successfully! I'll get back to you soon.
            </p>
            <p v-if="submitStatus === 'error'" class="contact__form-status contact__form-status--error">
              ✕ Something went wrong. Please try emailing me directly.
            </p>
            <p class="contact__form-note text-xs">
              Powered by <a href="https://web3forms.com" target="_blank" rel="noopener noreferrer">Web3Forms</a>.
            </p>
          </form>
        </ScrollReveal>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'
import SectionHeader from '../ui/SectionHeader.vue'
import ScrollReveal from '../ui/ScrollReveal.vue'
import personal from '../../data/personal.json'

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: '',
})

const isSubmitting = ref(false)
const submitStatus = ref('')

// Replace with your Web3Forms access key
const WEB3FORMS_KEY = import.meta.env.VITE_WEB3FORMS_ACCESS_KEY || 'YOUR_WEB3FORMS_ACCESS_KEY'

async function handleSubmit() {
  if (WEB3FORMS_KEY === 'YOUR_WEB3FORMS_ACCESS_KEY') {
    submitStatus.value = 'error'
    console.warn('Web3Forms access key not configured. Get one at https://web3forms.com')
    return
  }

  isSubmitting.value = true
  submitStatus.value = ''

  try {
    const response = await fetch('https://api.web3forms.com/submit', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        access_key: WEB3FORMS_KEY,
        name: form.name,
        email: form.email,
        subject: form.subject,
        message: form.message,
      }),
    })

    const result = await response.json()
    if (result.success) {
      submitStatus.value = 'success'
      form.name = ''
      form.email = ''
      form.subject = ''
      form.message = ''
    } else {
      submitStatus.value = 'error'
    }
  } catch {
    submitStatus.value = 'error'
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
.contact__grid {
  display: grid;
  grid-template-columns: 1fr 1.3fr;
  gap: var(--space-8);
  align-items: start;
}

.contact__info {
  display: flex;
  flex-direction: column;
  gap: var(--space-4);
}

.contact__info-card {
  display: flex;
  align-items: center;
  gap: var(--space-4);
  padding: var(--space-5);
}

.contact__info-card:hover {
  transform: none;
}

.contact__info-icon {
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--radius-md);
  background: var(--color-accent-glow);
  color: var(--color-accent);
  flex-shrink: 0;
}

.contact__info-card h4 {
  font-size: var(--text-sm);
  font-weight: 600;
  margin-bottom: var(--space-1);
}

.contact__info-card a {
  font-size: var(--text-sm);
  color: var(--color-text-secondary);
  word-break: break-all;
}

.contact__info-card a:hover {
  color: var(--color-accent);
}

.contact__form {
  display: flex;
  flex-direction: column;
  gap: var(--space-5);
}

.contact__form:hover {
  transform: none;
}

.contact__form-title {
  font-size: var(--text-xl);
  margin-bottom: var(--space-2);
}

.contact__form-group {
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
}

.contact__form-group label {
  font-size: var(--text-sm);
  font-weight: 500;
  color: var(--color-text-secondary);
}

.contact__form-group input,
.contact__form-group textarea {
  background: var(--color-bg-tertiary);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-sm);
  padding: var(--space-3) var(--space-4);
  font-family: var(--font-sans);
  font-size: var(--text-sm);
  color: var(--color-text-primary);
  transition: border-color var(--transition-fast);
  outline: none;
}

.contact__form-group input::placeholder,
.contact__form-group textarea::placeholder {
  color: var(--color-text-tertiary);
}

.contact__form-group input:focus,
.contact__form-group textarea:focus {
  border-color: var(--color-accent);
  box-shadow: 0 0 0 3px var(--color-accent-glow);
}

.contact__form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.contact__form-submit {
  align-self: flex-start;
}

.contact__form-submit:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.contact__form-status {
  font-size: var(--text-sm);
  padding: var(--space-3) var(--space-4);
  border-radius: var(--radius-sm);
}

.contact__form-status--success {
  color: var(--color-success);
  background: rgba(34, 197, 94, 0.1);
  border: 1px solid rgba(34, 197, 94, 0.2);
}

.contact__form-status--error {
  color: var(--color-error);
  background: rgba(239, 68, 68, 0.1);
  border: 1px solid rgba(239, 68, 68, 0.2);
}

.contact__form-note {
  color: var(--color-text-tertiary);
}

.contact__form-note a {
  color: var(--color-text-tertiary);
  text-decoration: underline;
}

@media (max-width: 768px) {
  .contact__grid {
    grid-template-columns: 1fr;
  }
}
</style>
