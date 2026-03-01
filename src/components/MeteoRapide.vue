<template>
  <div>
    <h2 class="text-lg font-semibold text-gray-800 mb-3">Météo rapide</h2>
    <div class="bg-white rounded-xl shadow-sm p-4">
      <div class="flex justify-between items-center mb-4">
        <div>
          <p class="text-3xl font-bold text-gray-800">14°C</p>
          <p class="text-sm text-gray-500">Saint-Malo</p>
        </div>
        <span class="text-5xl">☀️</span>
      </div>
      <div class="grid grid-cols-3 gap-2 text-center text-sm">
        <div v-for="jour in previsions" :key="jour.nom">
          <p class="text-gray-500">{{ jour.nom }}</p>
          <p class="font-medium">{{ jour.icone }} {{ jour.temp }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const previsions = [
  { nom: 'Auj.', icone: '☀️', temp: '14°' },
  { nom: 'Dim', icone: '⛅', temp: '12°' },
  { nom: 'Lun', icone: '🌧', temp: '10°' }
]
</script>