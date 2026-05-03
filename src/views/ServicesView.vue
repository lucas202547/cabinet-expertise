<template>
  <main>

    <!-- Bandeau titre -->
    <section class="bg-gradient-to-br from-slate-900 to-blue-900 text-white py-16 px-6 text-center">
      <h1 class="text-4xl font-bold mb-3">Nos Services</h1>
      <p class="text-slate-300 max-w-xl mx-auto">
        Un accompagnement global et personnalisé pour répondre à tous vos besoins
        comptables, fiscaux et stratégiques.
      </p>
    </section>

    <!-- Grille services -->
    <section class="py-20 px-6">
      <div class="max-w-5xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-8">
        <article
          v-for="service in services"
          :key="service.title"
          class="bg-white border border-slate-100 rounded-2xl shadow-sm hover:shadow-md transition-shadow p-8 flex gap-5"
        >
          <div
            :class="`flex-shrink-0 w-14 h-14 rounded-xl flex items-center justify-center text-2xl ${service.accent}`"
          >
            {{ service.icon }}
          </div>
          <div>
            <h2 class="text-lg font-bold text-slate-900 mb-2">{{ service.title }}</h2>
            <p class="text-slate-500 text-sm leading-relaxed">{{ service.description }}</p>
          </div>
        </article>
      </div>
    </section>

    <!-- CTA bas de page -->
    <section class="bg-slate-50 border-t border-slate-100 py-16 px-6 text-center">
      <h2 class="text-2xl font-bold text-slate-900 mb-3">
        Vous ne trouvez pas ce que vous cherchez ?
      </h2>
      <p class="text-slate-500 mb-8 max-w-lg mx-auto">
        Nos experts étudient chaque situation individuellement.
        Contactez-nous pour un premier échange gratuit.
      </p>
      <RouterLink
        to="/contact"
        class="inline-block bg-blue-800 hover:bg-blue-700 text-white px-8 py-3.5 rounded-lg font-semibold transition-colors"
      >
        Prendre rendez-vous
      </RouterLink>
    </section>

  </main>
</template>

<script setup>
const services = [
  {
    icon: '📒',
    title: 'Comptabilité générale',
    accent: 'bg-blue-100 text-blue-700',
    description:
      'Tenue et organisation de votre comptabilité au quotidien : saisie des pièces, rapprochements bancaires, gestion des tiers et suivi rigoureux de vos flux financiers.',
  },
  {
    icon: '📊',
    title: 'Établissement des bilans',
    accent: 'bg-indigo-100 text-indigo-700',
    description:
      'Préparation des comptes annuels, bilan, compte de résultat et annexes. Liasses fiscales conformes aux obligations légales, avec analyse de vos indicateurs clés.',
  },
  {
    icon: '🧾',
    title: 'Déclarations fiscales',
    accent: 'bg-sky-100 text-sky-700',
    description:
      'Établissement et dépôt de toutes vos déclarations : TVA, IS, IR, CFE, CVAE. Respect des échéances et veille permanente sur les évolutions réglementaires.',
  },
  {
    icon: '💼',
    title: 'Optimisation fiscale',
    accent: 'bg-emerald-100 text-emerald-700',
    description:
      'Analyse de votre situation fiscale pour réduire légalement votre charge d\'impôt. Choix du régime, stratégies d\'amortissement, gestion des déficits et planification patrimoniale.',
  },
  {
    icon: '🔍',
    title: 'Audit légal',
    accent: 'bg-amber-100 text-amber-700',
    description:
      'Commissariat aux comptes, certification des bilans et audit contractuel. Nos commissaires garantissent la fiabilité de vos informations financières auprès de vos partenaires.',
  },
  {
    icon: '📈',
    title: 'Conseil en gestion',
    accent: 'bg-rose-100 text-rose-700',
    description:
      'Tableaux de bord, analyse de performance, prévisionnels financiers et aide à la décision stratégique. Nous vous donnons les clés pour piloter votre activité avec sérénité.',
  },
]
</script>
