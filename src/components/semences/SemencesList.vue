<template>
  <div class="min-h-screen bg-gray-50">
    <!-- En-tête fixe -->
    <div class="bg-gradient-to-r from-green-600 to-green-500 text-white px-4 py-6 fixed top-0 left-0 right-0 z-10 shadow-lg">
      <h1 class="text-2xl font-bold">🌱 Mon Jardin Bio</h1>
      <p class="text-green-100 text-sm mt-1">{{ semencesFiltrees.length }} variétés</p>
    </div>

    <!-- Contenu principal (avec padding pour l'en-tête fixe) -->
    <div class="pt-24 pb-20 px-4">
      <!-- Mode LISTE -->
      <div v-if="!selectedSemence">
        <!-- Barre de recherche -->
        <div class="mb-4">
          <div class="relative">
            <span class="absolute left-3 top-3 text-gray-400">🔍</span>
            <input 
              v-model="recherche"
              type="text"
              placeholder="Rechercher..."
              class="w-full pl-10 pr-4 py-3 bg-white border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-transparent text-base"
            >
          </div>
        </div>

        <!-- Filtres par catégorie (scrollable horizontalement) -->
        <div class="mb-6 overflow-x-auto whitespace-nowrap pb-2 -mx-4 px-4">
          <button 
            @click="categorieSelectionnee = ''"
            class="inline-block px-4 py-2 rounded-full text-sm font-medium transition-all mr-2"
            :class="categorieSelectionnee === '' 
              ? 'bg-green-600 text-white shadow-md' 
              : 'bg-white text-gray-700 border border-gray-200'"
          >
            Toutes
          </button>
          <button 
            v-for="categorie in categories" 
            :key="categorie"
            @click="categorieSelectionnee = categorie"
            class="inline-block px-4 py-2 rounded-full text-sm font-medium transition-all mr-2"
            :class="categorieSelectionnee === categorie 
              ? getCategoryColor(categorie) + ' text-white shadow-md' 
              : 'bg-white text-gray-700 border border-gray-200'"
          >
            {{ categorie }}
          </button>
        </div>

        <!-- Grille de cartes (1 colonne sur mobile) -->
        <div class="space-y-4">
          <div 
            v-for="semence in semencesFiltrees" 
            :key="semence.nom"
            @click="selectedSemence = semence"
            class="bg-white rounded-xl shadow-sm hover:shadow-md transition-all duration-300 cursor-pointer active:scale-[0.98] overflow-hidden border border-gray-100"
          >
            <!-- Bandeau couleur -->
            <div :class="getCategoryColor(semence.categorie) + ' h-1.5'"></div>
            
            <div class="p-4">
              <div class="flex justify-between items-start mb-2">
                <div>
                  <h3 class="text-lg font-semibold text-gray-800">{{ semence.nom }}</h3>
                  <p class="text-xs text-gray-500 italic">{{ semence.nom_latin }}</p>
                </div>
                <span :class="getCategoryColor(semence.categorie) + ' text-white text-xs px-2 py-1 rounded-full'">
                  {{ semence.categorie }}
                </span>
              </div>

              <p class="text-gray-600 text-sm mb-3 line-clamp-2">{{ semence.description }}</p>

              <!-- Infos en badges -->
              <div class="flex flex-wrap gap-1.5 mb-2">
                <span class="text-xs bg-gray-100 text-gray-700 px-2 py-1 rounded-full">
                  🌡️ {{ semence.temperature_levée.optimum }}°C
                </span>
                <span class="text-xs bg-gray-100 text-gray-700 px-2 py-1 rounded-full">
                  ⏱️ {{ semence.jours_levée.min }}-{{ semence.jours_levée.max }}j
                </span>
                <span class="text-xs bg-gray-100 text-gray-700 px-2 py-1 rounded-full">
                  📏 {{ semence.distance_plantation_cm }}cm
                </span>
                <span class="text-xs bg-gray-100 text-gray-700 px-2 py-1 rounded-full">
                  💧 {{ semence.arrosage }}
                </span>
              </div>

              <!-- Maladies (1 seule ligne) -->
              <div v-if="semence.maladies.length > 0" class="flex flex-wrap gap-1">
                <span 
                  v-for="maladie in semence.maladies.slice(0, 1)" 
                  :key="maladie"
                  class="text-xs bg-red-100 text-red-700 px-2 py-1 rounded-full"
                >
                  ⚠️ {{ maladie }}
                </span>
                <span v-if="semence.maladies.length > 1" class="text-xs text-gray-500">
                  +{{ semence.maladies.length - 1 }}
                </span>
              </div>
            </div>
          </div>
        </div>

        <!-- Message si aucun résultat -->
        <div v-if="semencesFiltrees.length === 0" class="text-center py-12">
          <p class="text-gray-500 text-lg">😕 Aucune variété trouvée</p>
          <p class="text-gray-400 text-sm">Essaie d'autres mots-clés</p>
        </div>
      </div>

      <!-- Mode DÉTAIL (mobile optimisé) -->
      <div v-else class="pb-4">
        <button 
          @click="selectedSemence = null"
          class="flex items-center text-green-600 mb-4"
        >
          ← Retour
        </button>

        <div class="bg-white rounded-xl shadow-sm overflow-hidden">
          <!-- En-tête couleur -->
          <div :class="getCategoryColor(selectedSemence.categorie) + ' p-4 text-white'">
            <h2 class="text-2xl font-bold">{{ selectedSemence.nom }}</h2>
            <p class="text-white/80 text-sm italic">{{ selectedSemence.nom_latin }}</p>
          </div>

          <div class="p-4 space-y-4">
            <p class="text-gray-700">{{ selectedSemence.description }}</p>

            <!-- Grille d'infos compacte -->
            <div class="grid grid-cols-2 gap-3">
              <div class="bg-orange-50 p-3 rounded-lg">
                <span class="text-xs text-orange-600 block">🌡️ Température</span>
                <span class="font-medium">{{ selectedSemence.temperature_levée.optimum }}°C</span>
              </div>
              <div class="bg-blue-50 p-3 rounded-lg">
                <span class="text-xs text-blue-600 block">⏱️ Levée</span>
                <span class="font-medium">{{ selectedSemence.jours_levée.min }}-{{ selectedSemence.jours_levée.max }}j</span>
              </div>
              <div class="bg-green-50 p-3 rounded-lg">
                <span class="text-xs text-green-600 block">📏 Distance</span>
                <span class="font-medium">{{ selectedSemence.distance_plantation_cm }}cm</span>
              </div>
              <div class="bg-purple-50 p-3 rounded-lg">
                <span class="text-xs text-purple-600 block">💧 Arrosage</span>
                <span class="font-medium">{{ selectedSemence.arrosage }}</span>
              </div>
            </div>

            <!-- Détails supplémentaires -->
            <div class="space-y-2">
              <div class="flex justify-between py-2 border-b">
                <span class="text-gray-600">Profondeur semis</span>
                <span class="font-medium">{{ selectedSemence.profondeur_semis_cm }} cm</span>
              </div>
              <div class="flex justify-between py-2 border-b">
                <span class="text-gray-600">Distance entre rangs</span>
                <span class="font-medium">{{ selectedSemence.distance_rang_cm }} cm</span>
              </div>
              <div class="flex justify-between py-2 border-b">
                <span class="text-gray-600">Lumière</span>
                <span class="font-medium">{{ selectedSemence.besoin_lumiere }}</span>
              </div>
              <div class="flex justify-between py-2 border-b">
                <span class="text-gray-600">Type de sol</span>
                <span class="font-medium">{{ selectedSemence.type_sol }}</span>
              </div>
              <div class="flex justify-between py-2 border-b">
                <span class="text-gray-600">Conservation</span>
                <span class="font-medium">{{ selectedSemence.duree_germination_ans }} ans</span>
              </div>
            </div>

            <!-- Maladies -->
            <div v-if="selectedSemence.maladies.length > 0">
              <h3 class="font-medium text-gray-700 mb-2">Maladies courantes</h3>
              <div class="flex flex-wrap gap-2">
                <span 
                  v-for="maladie in selectedSemence.maladies" 
                  :key="maladie"
                  class="px-3 py-1 bg-red-100 text-red-700 text-sm rounded-full"
                >
                  {{ maladie }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Barre de navigation mobile -->
    <div class="fixed bottom-0 left-0 right-0 bg-white border-t border-gray-200 px-6 py-2 flex justify-around items-center text-xs text-gray-500">
      <div class="flex flex-col items-center text-green-600">
        <span class="text-xl mb-1">🌱</span>
        <span>Semences</span>
      </div>
      <div class="flex flex-col items-center">
        <span class="text-xl mb-1">📅</span>
        <span>Planning</span>
      </div>
      <div class="flex flex-col items-center">
        <span class="text-xl mb-1">🌦️</span>
        <span>Météo</span>
      </div>
      <div class="flex flex-col items-center">
        <span class="text-xl mb-1">👤</span>
        <span>Profil</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import semencesData from '@/data/semences_complet.json'

const semences = semencesData.semences
const recherche = ref('')
const categorieSelectionnee = ref('')
const selectedSemence = ref(null)

const categories = [...new Set(semences.map(s => s.categorie))]

function getCategoryColor(categorie) {
  const colors = {
    'légume-fruit': 'bg-orange-500',
    'légume-racine': 'bg-purple-500',
    'légume-bulbe': 'bg-yellow-600',
    'légume-feuille': 'bg-green-500',
    'légume-fleur': 'bg-pink-500',
    'légume-graine': 'bg-amber-600',
    'légume-tige': 'bg-lime-600',
    'aromatique': 'bg-emerald-500',
    'fleur-comestible': 'bg-rose-500',
    'mini-légume': 'bg-indigo-500'
  }
  return colors[categorie] || 'bg-gray-500'
}

const semencesFiltrees = computed(() => {
  let result = semences
  if (categorieSelectionnee.value) {
    result = result.filter(s => s.categorie === categorieSelectionnee.value)
  }
  if (recherche.value) {
    const searchLower = recherche.value.toLowerCase()
    result = result.filter(s => 
      s.nom.toLowerCase().includes(searchLower) ||
      s.nom_latin.toLowerCase().includes(searchLower) ||
      s.description.toLowerCase().includes(searchLower) ||
      s.maladies.some(maladie => maladie.toLowerCase().includes(searchLower))
    )
  }
  return result
})

function nombreParCategorie(categorie) {
  return semences.filter(s => s.categorie === categorie).length
}
</script>

<style scoped>
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>