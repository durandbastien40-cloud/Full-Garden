<template>
  <div class="bg-white rounded-lg shadow-lg p-6">
    <h2 class="text-2xl font-bold text-green-800 mb-4">
      🌱 Catalogue des semences
    </h2>

    <!-- Filtres par catégorie -->
    <div class="flex flex-wrap gap-2 mb-6">
      <button 
        @click="categorieSelectionnee = ''"
        class="px-3 py-1 rounded-full text-sm"
        :class="categorieSelectionnee === '' ? 'bg-green-600 text-white' : 'bg-gray-200 text-gray-700'"
      >
        Toutes
      </button>
      <button 
        v-for="categorie in categories" 
        :key="categorie"
        @click="categorieSelectionnee = categorie"
        class="px-3 py-1 rounded-full text-sm"
        :class="categorieSelectionnee === categorie ? 'bg-green-600 text-white' : 'bg-gray-200 text-gray-700'"
      >
        {{ categorie }}
      </button>
    </div>

    <!-- Liste des semences -->
    <div class="space-y-4">
      <div 
        v-for="semence in semences" 
        :key="semence.nom"
        class="border border-gray-200 rounded-lg p-4 hover:shadow-md transition-shadow"
      >
        <div class="flex justify-between items-start">
          <div>
            <h3 class="text-lg font-semibold text-gray-800">{{ semence.nom }}</h3>
            <p class="text-sm text-gray-500 italic">{{ semence.nom_latin }}</p>
          </div>
          <span class="px-2 py-1 bg-green-100 text-green-800 text-xs rounded-full">
            {{ semence.categorie }}
          </span>
        </div>

        <p class="text-gray-600 text-sm mt-2">{{ semence.description }}</p>

        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mt-4 text-sm">
          <div>
            <span class="text-gray-500">🌡️ Levée</span>
            <p class="font-medium">{{ semence.temperature_levée.min }}-{{ semence.temperature_levée.optimum }}°C</p>
          </div>
          <div>
            <span class="text-gray-500">⏱️ Jours levée</span>
            <p class="font-medium">{{ semence.jours_levée.min }}-{{ semence.jours_levée.max }}j</p>
          </div>
          <div>
            <span class="text-gray-500">📏 Distance</span>
            <p class="font-medium">{{ semence.distance_plantation_cm }} cm</p>
          </div>
          <div>
            <span class="text-gray-500">💧 Arrosage</span>
            <p class="font-medium">{{ semence.arrosage }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import semencesData from '@/data/semences_complet.json'

const semences = semencesData.semences

// Extraire les catégories uniques
const categories = [...new Set(semences.map(s => s.categorie))]
const categorieSelectionnee = ''
</script>