<template>
  <div class="min-h-screen flex flex-col">
    <Navbar />
    <RouterView class="flex-1" />
    <Footer />
  </div>
</template>

<script setup>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'
</script>
