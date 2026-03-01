<template>
  <div class="bg-white rounded-lg shadow-lg p-6 mb-6">
    <div class="flex justify-between items-center mb-4">
      <h2 class="text-xl font-semibold text-gray-800">Météo du jour</h2>
      <span class="text-4xl">{{ meteo.icone }}</span>
    </div>
    
    <div class="flex items-center justify-between">
      <div>
        <p class="text-3xl font-bold text-gray-900">{{ meteo.temperature }}°C</p>
        <p class="text-gray-600">{{ meteo.ville }}</p>
      </div>
      
      <div class="text-right">
        <p class="text-sm text-gray-600">Humidité {{ meteo.humidite }}%</p>
        <p class="text-sm text-gray-600">Vent {{ meteo.vent }} km/h</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import meteoData from 'C:/Users/laure/mes-projets/mon-jardin-bio/src/data/meteo.json'

const meteo = meteoData
</script>