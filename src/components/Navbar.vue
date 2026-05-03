<template>
  <header class="bg-white shadow-sm sticky top-0 z-50">
    <nav class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between">
      <RouterLink to="/" class="text-xl font-bold text-slate-900 hover:text-blue-700 transition-colors">
        Durand & Associés
      </RouterLink>

      <ul class="hidden md:flex items-center gap-8">
        <li v-for="link in links" :key="link.to">
          <RouterLink
            :to="link.to"
            class="text-slate-600 hover:text-blue-700 font-medium transition-colors"
            active-class="text-blue-700 font-semibold"
          >
            {{ link.label }}
          </RouterLink>
        </li>
      </ul>

      <button
        class="md:hidden text-slate-700"
        @click="mobileOpen = !mobileOpen"
        aria-label="Menu"
      >
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path v-if="!mobileOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </nav>

    <div v-if="mobileOpen" class="md:hidden border-t border-slate-100 bg-white px-6 py-4 flex flex-col gap-4">
      <RouterLink
        v-for="link in links"
        :key="link.to"
        :to="link.to"
        class="text-slate-700 hover:text-blue-700 font-medium transition-colors"
        active-class="text-blue-700 font-semibold"
        @click="mobileOpen = false"
      >
        {{ link.label }}
      </RouterLink>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const mobileOpen = ref(false)

const links = [
  { to: '/', label: 'Accueil' },
  { to: '/services', label: 'Services' },
  { to: '/a-propos', label: 'À propos' },
  { to: '/contact', label: 'Contact' },
]
</script>
