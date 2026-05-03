<template>
  <main>

    <!-- Bandeau titre -->
    <section class="bg-gradient-to-br from-slate-900 to-blue-900 text-white py-16 px-6 text-center">
      <h1 class="text-4xl font-bold mb-3">À Propos</h1>
      <p class="text-slate-300 max-w-xl mx-auto">
        Un cabinet indépendant fondé sur la rigueur, la proximité et l'engagement
        durable envers ses clients.
      </p>
    </section>

    <!-- Présentation -->
    <section class="py-20 px-6">
      <div class="max-w-5xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
        <div>
          <p class="text-sm font-semibold text-blue-700 uppercase tracking-widest mb-3">Notre cabinet</p>
          <h2 class="text-3xl font-bold text-slate-900 mb-5 leading-snug">
            25 ans d'excellence au service des entreprises
          </h2>
          <p class="text-slate-500 leading-relaxed mb-4">
            Fondé par Maître Jean Durand, le cabinet s'est construit autour d'une conviction
            simple : la comptabilité doit être un levier de croissance, pas une contrainte.
            Nous apportons à chaque client une lecture claire et stratégique de sa situation financière.
          </p>
          <p class="text-slate-500 leading-relaxed">
            Aujourd'hui, notre équipe de 12 professionnels accompagne plus de 500 entreprises,
            professions libérales et particuliers à Paris et en Île-de-France.
          </p>
        </div>

        <div class="grid grid-cols-2 gap-4">
          <div
            v-for="val in values"
            :key="val.title"
            class="bg-slate-50 border border-slate-100 rounded-xl p-6"
          >
            <div class="text-2xl mb-3">{{ val.icon }}</div>
            <div class="font-semibold text-slate-900 mb-1 text-sm">{{ val.title }}</div>
            <div class="text-xs text-slate-500 leading-relaxed">{{ val.detail }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Équipe -->
    <section class="py-20 px-6 bg-slate-50">
      <div class="max-w-5xl mx-auto">
        <div class="text-center mb-12">
          <p class="text-sm font-semibold text-blue-700 uppercase tracking-widest mb-2">L'équipe</p>
          <h2 class="text-3xl font-bold text-slate-900">Des experts à votre écoute</h2>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-3 gap-8">
          <div
            v-for="member in team"
            :key="member.name"
            class="bg-white border border-slate-100 rounded-2xl shadow-sm p-8 text-center hover:shadow-md transition-shadow"
          >
            <!-- Photo placeholder -->
            <div class="w-24 h-24 rounded-full bg-slate-200 mx-auto mb-5 flex items-center justify-center">
              <span class="text-3xl font-bold text-slate-400">{{ member.initials }}</span>
            </div>
            <div class="font-bold text-slate-900 text-lg mb-1">{{ member.name }}</div>
            <div class="text-sm text-blue-700 font-medium mb-3">{{ member.title }}</div>
            <p class="text-xs text-slate-500 leading-relaxed">{{ member.bio }}</p>
            <div class="mt-4 flex flex-wrap gap-2 justify-center">
              <span
                v-for="tag in member.tags"
                :key="tag"
                class="bg-slate-100 text-slate-600 text-xs px-2.5 py-1 rounded-full"
              >
                {{ tag }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Timeline -->
    <section class="py-20 px-6">
      <div class="max-w-3xl mx-auto">
        <div class="text-center mb-14">
          <p class="text-sm font-semibold text-blue-700 uppercase tracking-widest mb-2">Notre histoire</p>
          <h2 class="text-3xl font-bold text-slate-900">Les grandes étapes du cabinet</h2>
        </div>

        <div class="relative">
          <!-- Ligne verticale -->
          <div class="absolute left-1/2 -translate-x-1/2 top-0 bottom-0 w-px bg-slate-200 hidden md:block" />

          <div class="space-y-10">
            <div
              v-for="(event, index) in timeline"
              :key="event.year"
              class="relative flex flex-col md:flex-row items-start md:items-center gap-6"
              :class="index % 2 === 0 ? 'md:flex-row' : 'md:flex-row-reverse'"
            >
              <!-- Contenu -->
              <div class="md:w-5/12" :class="index % 2 === 0 ? 'md:text-right' : 'md:text-left'">
                <div class="bg-white border border-slate-100 rounded-xl shadow-sm p-6">
                  <div class="font-bold text-slate-500 text-xs uppercase tracking-widest mb-1">
                    {{ event.year }}
                  </div>
                  <div class="font-bold text-slate-900 mb-2">{{ event.title }}</div>
                  <p class="text-sm text-slate-500 leading-relaxed">{{ event.description }}</p>
                </div>
              </div>

              <!-- Point central -->
              <div class="hidden md:flex w-2/12 justify-center flex-shrink-0 z-10">
                <div class="w-10 h-10 rounded-full bg-blue-700 text-white text-sm font-bold flex items-center justify-center shadow-md">
                  {{ event.year.slice(2) }}
                </div>
              </div>

              <!-- Espace opposé -->
              <div class="md:w-5/12 hidden md:block" />
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="bg-slate-900 py-16 px-6 text-white text-center">
      <h2 class="text-2xl font-bold mb-3">Rejoignez nos clients</h2>
      <p class="text-slate-400 mb-8 max-w-md mx-auto">
        Découvrez comment notre équipe peut vous accompagner dans votre développement.
      </p>
      <RouterLink
        to="/contact"
        class="inline-block bg-blue-600 hover:bg-blue-500 text-white px-8 py-3.5 rounded-lg font-semibold transition-colors"
      >
        Nous contacter
      </RouterLink>
    </section>

  </main>
</template>

<script setup>
const values = [
  { icon: '🎯', title: 'Rigueur', detail: 'Chaque chiffre est vérifié, chaque délai respecté.' },
  { icon: '🤝', title: 'Proximité', detail: 'Un interlocuteur dédié qui connaît votre dossier.' },
  { icon: '🔒', title: 'Confidentialité', detail: 'Vos données financières restent strictement protégées.' },
  { icon: '📡', title: 'Innovation', detail: 'Outils numériques et reporting en temps réel.' },
]

const team = [
  {
    name: 'Jean Durand',
    initials: 'JD',
    title: 'Expert-comptable fondateur',
    bio: 'Diplômé de l\'INTEC, Jean a fondé le cabinet en 1998 après 10 ans en cabinet international. Spécialiste de la fiscalité des PME.',
    tags: ['Fiscalité', 'PME', 'Stratégie'],
  },
  {
    name: 'Sophie Martin',
    initials: 'SM',
    title: 'Commissaire aux comptes',
    bio: 'Inscrite à la Compagnie Nationale des Commissaires aux Comptes, Sophie intervient principalement sur les missions d\'audit légal et contractuel.',
    tags: ['Audit', 'Commissariat', 'Due diligence'],
  },
  {
    name: 'Thomas Leblanc',
    initials: 'TL',
    title: 'Responsable fiscal & social',
    bio: 'Master 2 en droit fiscal à Paris II, Thomas gère l\'ensemble des déclarations fiscales et conseille les dirigeants sur l\'optimisation de leur rémunération.',
    tags: ['Droit fiscal', 'Paie', 'Optimisation'],
  },
]

const timeline = [
  {
    year: '2000',
    title: 'Fondation du cabinet',
    description:
      'Jean Durand ouvre les portes du cabinet rue de la République avec une équipe de 3 personnes et une vingtaine de clients fondateurs.',
  },
  {
    year: '2010',
    title: 'Développement et spécialisation',
    description:
      'Ouverture d\'un pôle audit avec l\'arrivée de Sophie Martin. Le cabinet dépasse les 150 clients et se spécialise dans l\'accompagnement des professions libérales.',
  },
  {
    year: '2018',
    title: 'Transformation numérique',
    description:
      'Déploiement d\'un espace client en ligne sécurisé et migration vers des outils comptables cloud. Gain de temps et transparence accrue pour tous les clients.',
  },
  {
    year: '2024',
    title: 'Nouveau cap : 500 clients',
    description:
      'Le cabinet franchit le cap des 500 clients accompagnés et renforce son équipe pour répondre à la croissance. Lancement d\'un service de conseil en financement.',
  },
]
</script>
