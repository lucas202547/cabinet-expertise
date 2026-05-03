<template>
  <main>
    <!-- En-tête -->
    <section class="bg-gradient-to-br from-slate-900 to-blue-900 text-white py-16 px-6 text-center">
      <h1 class="text-4xl font-bold mb-3">Nous Contacter</h1>
      <p class="text-slate-300 max-w-xl mx-auto">
        Nos équipes sont disponibles du lundi au vendredi de 9h à 18h.
        Réponse garantie sous 24h.
      </p>
    </section>

    <!-- Contenu principal -->
    <section class="py-16 px-6">
      <div class="max-w-5xl mx-auto grid grid-cols-1 lg:grid-cols-5 gap-12">

        <!-- Formulaire -->
        <div class="lg:col-span-3">

          <!-- Succès -->
          <div
            v-if="status === 'success'"
            class="mb-6 flex items-start gap-3 bg-green-50 border border-green-200 text-green-800 rounded-xl p-5"
          >
            <span class="text-xl">✅</span>
            <div>
              <p class="font-semibold">Message envoyé avec succès !</p>
              <p class="text-sm text-green-700 mt-0.5">
                Nous reviendrons vers vous dans les meilleurs délais.
              </p>
            </div>
          </div>

          <!-- Erreur -->
          <div
            v-if="status === 'error'"
            class="mb-6 flex items-start gap-3 bg-red-50 border border-red-200 text-red-800 rounded-xl p-5"
          >
            <span class="text-xl">⚠️</span>
            <div>
              <p class="font-semibold">Une erreur est survenue.</p>
              <p class="text-sm text-red-700 mt-0.5">
                {{ errorMessage }}
              </p>
            </div>
          </div>

          <form
            v-if="status !== 'success'"
            @submit.prevent="handleSubmit"
            novalidate
            class="space-y-5"
          >
            <!-- Nom -->
            <div>
              <label for="name" class="block text-sm font-medium text-slate-700 mb-1">
                Nom complet <span class="text-red-500">*</span>
              </label>
              <input
                id="name"
                v-model.trim="form.name"
                type="text"
                placeholder="Jean Dupont"
                :class="fieldClass('name')"
                @blur="touch('name')"
              />
              <p v-if="errors.name" class="mt-1.5 text-xs text-red-600">{{ errors.name }}</p>
            </div>

            <!-- Email -->
            <div>
              <label for="email" class="block text-sm font-medium text-slate-700 mb-1">
                Adresse email <span class="text-red-500">*</span>
              </label>
              <input
                id="email"
                v-model.trim="form.email"
                type="email"
                placeholder="jean@exemple.fr"
                :class="fieldClass('email')"
                @blur="touch('email')"
              />
              <p v-if="errors.email" class="mt-1.5 text-xs text-red-600">{{ errors.email }}</p>
            </div>

            <!-- Téléphone -->
            <div>
              <label for="phone" class="block text-sm font-medium text-slate-700 mb-1">
                Téléphone
                <span class="text-slate-400 font-normal">(optionnel)</span>
              </label>
              <input
                id="phone"
                v-model.trim="form.phone"
                type="tel"
                placeholder="06 12 34 56 78"
                class="w-full border border-slate-300 rounded-lg px-4 py-2.5 text-slate-900 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition"
              />
            </div>

            <!-- Sujet -->
            <div>
              <label for="subject" class="block text-sm font-medium text-slate-700 mb-1">
                Sujet <span class="text-red-500">*</span>
              </label>
              <select
                id="subject"
                v-model="form.subject"
                :class="fieldClass('subject')"
                @blur="touch('subject')"
              >
                <option value="" disabled>Choisissez un sujet</option>
                <option value="Comptabilité">Comptabilité</option>
                <option value="Fiscalité">Fiscalité</option>
                <option value="Audit">Audit</option>
                <option value="Autre">Autre</option>
              </select>
              <p v-if="errors.subject" class="mt-1.5 text-xs text-red-600">{{ errors.subject }}</p>
            </div>

            <!-- Message -->
            <div>
              <label for="message" class="block text-sm font-medium text-slate-700 mb-1">
                Message <span class="text-red-500">*</span>
              </label>
              <textarea
                id="message"
                v-model.trim="form.message"
                rows="5"
                placeholder="Décrivez votre besoin..."
                :class="fieldClass('message')"
                @blur="touch('message')"
                class="resize-none"
              />
              <p v-if="errors.message" class="mt-1.5 text-xs text-red-600">{{ errors.message }}</p>
            </div>

            <!-- Submit -->
            <button
              type="submit"
              :disabled="loading"
              class="w-full bg-blue-800 hover:bg-blue-700 disabled:bg-blue-300 text-white py-3.5 rounded-lg font-semibold transition-colors flex items-center justify-center gap-2"
            >
              <svg v-if="loading" class="animate-spin h-5 w-5" fill="none" viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4" />
                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8v8z" />
              </svg>
              {{ loading ? 'Envoi en cours...' : 'Envoyer le message' }}
            </button>

            <p class="text-xs text-slate-400 text-center">
              Les champs marqués <span class="text-red-500">*</span> sont obligatoires.
            </p>
          </form>
        </div>

        <!-- Coordonnées -->
        <aside class="lg:col-span-2 space-y-6">
          <div class="bg-slate-50 border border-slate-100 rounded-xl p-8 space-y-7">
            <div
              v-for="info in contactInfo"
              :key="info.label"
              class="flex items-start gap-4"
            >
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-700 flex items-center justify-center text-lg flex-shrink-0">
                {{ info.icon }}
              </div>
              <div>
                <div class="text-sm font-semibold text-slate-900 mb-1">{{ info.label }}</div>
                <div
                  v-for="line in info.lines"
                  :key="line"
                  class="text-sm text-slate-500"
                >
                  {{ line }}
                </div>
              </div>
            </div>
          </div>

          <div class="bg-blue-50 border border-blue-100 rounded-xl p-6">
            <p class="text-sm font-semibold text-blue-900 mb-1">Premier contact gratuit</p>
            <p class="text-sm text-blue-700 leading-relaxed">
              Nous proposons un premier rendez-vous d'une heure, sans engagement,
              pour étudier votre situation et vous orienter vers la solution adaptée.
            </p>
          </div>
        </aside>

      </div>
    </section>
  </main>
</template>

<script setup>
import { reactive, ref } from 'vue'
import { createClient } from '@supabase/supabase-js'

const supabase = createClient(
  import.meta.env.VITE_SUPABASE_URL,
  import.meta.env.VITE_SUPABASE_ANON_KEY,
)

// --- État ---
const form = reactive({
  name: '',
  email: '',
  phone: '',
  subject: '',
  message: '',
})

const touched = reactive({})
const errors = reactive({})
const loading = ref(false)
const status = ref('idle') // 'idle' | 'success' | 'error'
const errorMessage = ref('')

// --- Validation ---
const EMAIL_RE = /^[^\s@]+@[^\s@]+\.[^\s@]+$/

function validate() {
  const e = {}
  if (!form.name) e.name = 'Le nom est requis.'
  if (!form.email) {
    e.email = "L'email est requis."
  } else if (!EMAIL_RE.test(form.email)) {
    e.email = 'Veuillez saisir une adresse email valide.'
  }
  if (!form.subject) e.subject = 'Veuillez sélectionner un sujet.'
  if (!form.message) {
    e.message = 'Le message est requis.'
  } else if (form.message.length < 10) {
    e.message = 'Le message doit contenir au moins 10 caractères.'
  }
  Object.assign(errors, { name: null, email: null, subject: null, message: null, ...e })
  return Object.keys(e).length === 0
}

function touch(field) {
  touched[field] = true
  validate()
}

// --- Classes dynamiques ---
const BASE_FIELD =
  'w-full border rounded-lg px-4 py-2.5 text-slate-900 placeholder-slate-400 focus:outline-none focus:ring-2 transition'

function fieldClass(field) {
  const hasError = touched[field] && errors[field]
  return [
    BASE_FIELD,
    hasError
      ? 'border-red-400 focus:ring-red-400 bg-red-50'
      : 'border-slate-300 focus:ring-blue-500 focus:border-blue-500',
  ]
}

// --- Soumission ---
async function handleSubmit() {
  Object.keys(form).forEach((k) => (touched[k] = true))
  if (!validate()) return

  loading.value = true
  status.value = 'idle'

  const { error } = await supabase.from('contacts').insert({
    nom: form.name,
    email: form.email,
    telephone: form.phone || null,
    sujet: form.subject,
    message: form.message,
  })

  loading.value = false

  if (error) {
    status.value = 'error'
    errorMessage.value =
      error.message || "Impossible d'envoyer le message. Veuillez réessayer."
  } else {
    status.value = 'success'
  }
}

// --- Données statiques ---
const contactInfo = [
  {
    icon: '📍',
    label: 'Adresse',
    lines: ['12 rue de la République', '75001 Paris'],
  },
  {
    icon: '📞',
    label: 'Téléphone',
    lines: ['01 23 45 67 89'],
  },
  {
    icon: '✉️',
    label: 'Email',
    lines: ['contact@durand-associes.fr'],
  },
  {
    icon: '🕐',
    label: 'Horaires',
    lines: ['Lundi – Vendredi : 9h – 18h', 'Samedi : sur rendez-vous'],
  },
]
</script>
