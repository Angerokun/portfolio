<template>
  <div id="portfolio-app">
    <Navbar />
    <main>
      <RouterView />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Navbar from './components/layout/Navbar.vue'
import Footer from './components/layout/Footer.vue'
</script>

<style>
#portfolio-app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  flex: 1;
}
</style>
