<template>
  <main>

    <!-- HERO -->
    <section class="bg-gradient-to-br from-slate-900 to-blue-900 text-white py-28 px-6">
      <div class="max-w-4xl mx-auto text-center">
        <p class="text-blue-300 text-sm font-semibold uppercase tracking-widest mb-4">
          Cabinet d'expertise comptable depuis 1998
        </p>
        <h1 class="text-4xl md:text-6xl font-bold leading-tight mb-6">
          Votre partenaire comptable<br class="hidden md:block" />
          <span class="text-blue-300">de confiance</span>
        </h1>
        <p class="text-slate-300 text-lg md:text-xl max-w-2xl mx-auto mb-10 leading-relaxed">
          Nous accompagnons dirigeants, PME et indépendants dans leur gestion comptable,
          fiscale et stratégique avec rigueur et proximité.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <RouterLink
            to="/services"
            class="bg-blue-600 hover:bg-blue-500 text-white px-8 py-3.5 rounded-lg font-semibold transition-colors"
          >
            Nos services
          </RouterLink>
          <RouterLink
            to="/contact"
            class="bg-white/10 hover:bg-white/20 text-white border border-white/30 px-8 py-3.5 rounded-lg font-semibold transition-colors"
          >
            Nous contacter
          </RouterLink>
        </div>
      </div>
    </section>

    <!-- STATS -->
    <section class="py-16 px-6 bg-white">
      <div class="max-w-5xl mx-auto grid grid-cols-1 sm:grid-cols-3 gap-6">
        <div
          v-for="stat in stats"
          :key="stat.label"
          class="bg-white rounded-xl shadow-md border border-slate-100 p-8 text-center"
        >
          <div class="text-4xl font-bold text-blue-700 mb-2">{{ stat.value }}</div>
          <div class="text-slate-500 font-medium">{{ stat.label }}</div>
        </div>
      </div>
    </section>

    <!-- SERVICES -->
    <section class="py-20 px-6 bg-slate-50">
      <div class="max-w-5xl mx-auto">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-slate-900 mb-3">Nos expertises</h2>
          <p class="text-slate-500 max-w-xl mx-auto">
            Un accompagnement sur mesure pour chaque étape de la vie de votre entreprise.
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div
            v-for="service in services"
            :key="service.title"
            class="bg-white rounded-xl shadow-sm border border-slate-100 p-8 hover:shadow-md transition-shadow"
          >
            <div class="text-4xl mb-5">{{ service.icon }}</div>
            <h3 class="text-lg font-bold text-slate-900 mb-3">{{ service.title }}</h3>
            <p class="text-slate-500 text-sm leading-relaxed">{{ service.description }}</p>
          </div>
        </div>

        <div class="text-center mt-10">
          <RouterLink
            to="/services"
            class="inline-block text-blue-700 font-semibold hover:text-blue-900 border-b-2 border-blue-200 hover:border-blue-700 transition-colors pb-0.5"
          >
            Voir tous nos services →
          </RouterLink>
        </div>
      </div>
    </section>

    <!-- POURQUOI NOUS -->
    <section class="py-20 px-6 bg-white">
      <div class="max-w-5xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
        <div>
          <h2 class="text-3xl font-bold text-slate-900 mb-4">
            Pourquoi choisir Durand & Associés ?
          </h2>
          <p class="text-slate-500 mb-8 leading-relaxed">
            Nous construisons avec chaque client une relation durable fondée sur la confiance,
            la réactivité et l'excellence professionnelle.
          </p>
          <ul class="space-y-4">
            <li
              v-for="point in strengths"
              :key="point.title"
              class="flex items-start gap-4"
            >
              <span class="flex-shrink-0 w-6 h-6 rounded-full bg-blue-100 text-blue-700 flex items-center justify-center font-bold text-sm mt-0.5">
                ✓
              </span>
              <div>
                <span class="font-semibold text-slate-800">{{ point.title }}</span>
                <span class="text-slate-500"> — {{ point.detail }}</span>
              </div>
            </li>
          </ul>
        </div>

        <div class="bg-slate-50 rounded-2xl p-10 border border-slate-100 space-y-6">
          <div
            v-for="item in testimonial"
            :key="item.name"
            class="border-l-4 border-blue-600 pl-5"
          >
            <p class="text-slate-600 italic text-sm leading-relaxed mb-3">
              "{{ item.quote }}"
            </p>
            <div class="text-sm font-semibold text-slate-800">{{ item.name }}</div>
            <div class="text-xs text-slate-400">{{ item.role }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA FINAL -->
    <section class="bg-slate-900 py-20 px-6 text-white text-center">
      <div class="max-w-2xl mx-auto">
        <h2 class="text-3xl font-bold mb-4">
          Prêt à simplifier votre comptabilité ?
        </h2>
        <p class="text-slate-400 mb-8 text-lg leading-relaxed">
          Prenez rendez-vous avec l'un de nos experts pour un premier échange gratuit
          et sans engagement.
        </p>
        <RouterLink
          to="/contact"
          class="inline-block bg-blue-600 hover:bg-blue-500 text-white px-10 py-4 rounded-lg font-semibold text-lg transition-colors shadow-lg shadow-blue-900/40"
        >
          Prendre rendez-vous
        </RouterLink>
      </div>
    </section>

  </main>
</template>

<script setup>
const stats = [
  { value: '25 ans', label: "d'expérience" },
  { value: '500+', label: 'clients accompagnés' },
  { value: '98%', label: 'de satisfaction client' },
]

const services = [
  {
    icon: '📊',
    title: 'Comptabilité & Bilan',
    description:
      'Tenue comptable, établissement des comptes annuels, bilans et liasses fiscales pour les entreprises de toutes tailles.',
  },
  {
    icon: '💼',
    title: 'Conseil fiscal',
    description:
      'Optimisation fiscale, déclarations IS/IR/TVA, gestion des contrôles fiscaux et planification patrimoniale.',
  },
  {
    icon: '📋',
    title: 'Audit & Commissariat',
    description:
      'Audit légal et contractuel, certification des comptes, contrôle interne et accompagnement des due diligences.',
  },
]

const strengths = [
  {
    title: 'Équipe dédiée',
    detail: 'un interlocuteur unique qui connaît votre dossier en profondeur',
  },
  {
    title: 'Réactivité garantie',
    detail: 'réponse sous 24h à toute demande client',
  },
  {
    title: 'Veille réglementaire',
    detail: 'formation continue de nos experts sur les évolutions fiscales et légales',
  },
  {
    title: 'Outils numériques',
    detail: 'accès client en ligne, dépôt de documents sécurisé et reporting en temps réel',
  },
]

const testimonial = [
  {
    quote:
      "Le cabinet Durand nous accompagne depuis la création de notre PME. Leur disponibilité et leur expertise nous ont permis d'aborder sereinement notre première levée de fonds.",
    name: 'Marie L.',
    role: 'Dirigeante, société de conseil – Paris',
  },
  {
    quote:
      "Enfin un cabinet qui explique les choses clairement. J'ai une vision nette de ma situation fiscale pour la première fois depuis des années.",
    name: 'Philippe R.',
    role: 'Médecin libéral – Lyon',
  },
]
</script>
