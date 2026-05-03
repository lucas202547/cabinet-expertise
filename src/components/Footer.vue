<template>
  <footer class="bg-slate-900 text-slate-300 mt-auto">
    <div class="max-w-6xl mx-auto px-6 py-12 grid grid-cols-1 md:grid-cols-3 gap-10">
      <div>
        <div class="text-white font-bold text-lg mb-3">Durand & Associés</div>
        <p class="text-sm text-slate-400 leading-relaxed">
          Cabinet d'experts-comptables indépendant, accompagnant entreprises et particuliers depuis 1998.
        </p>
      </div>

      <div>
        <div class="text-white font-semibold mb-3">Liens rapides</div>
        <ul class="space-y-2 text-sm">
          <li v-for="link in links" :key="link.to">
            <RouterLink :to="link.to" class="hover:text-white transition-colors">
              {{ link.label }}
            </RouterLink>
          </li>
        </ul>
      </div>

      <div>
        <div class="text-white font-semibold mb-3">Contact</div>
        <ul class="space-y-2 text-sm text-slate-400">
          <li>12 rue de la République, 75001 Paris</li>
          <li>01 23 45 67 89</li>
          <li>contact@durand-associes.fr</li>
        </ul>
      </div>
    </div>

    <div class="border-t border-slate-800 text-center text-sm text-slate-500 py-4">
      © 2024 Cabinet Durand & Associés. Tous droits réservés.
    </div>
  </footer>
</template>

<script setup>
const links = [
  { to: '/', label: 'Accueil' },
  { to: '/services', label: 'Services' },
  { to: '/a-propos', label: 'À propos' },
  { to: '/contact', label: 'Contact' },
]
</script>
