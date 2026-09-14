<template>
  <div ref="el" class="reveal" :class="[delayClass]">
    <slot />
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  delay: { type: Number, default: 0 },
  threshold: { type: Number, default: 0.15 },
})

const el = ref(null)
let observer = null

const delayClass = computed(() => {
  if (props.delay > 0 && props.delay <= 5) {
    return `reveal-delay-${props.delay}`
  }
  return ''
})

onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('revealed')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: props.threshold }
  )

  if (el.value) {
    observer.observe(el.value)
  }
})

onUnmounted(() => {
  if (observer) {
    observer.disconnect()
  }
})
</script>
