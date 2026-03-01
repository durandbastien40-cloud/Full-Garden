<template>
  <div class="grid grid-cols-2 gap-3">
    <div v-for="stat in stats" :key="stat.label" class="bg-white rounded-xl shadow-sm p-4">
      <p class="text-gray-500 text-xs">{{ stat.label }}</p>
      <p class="text-2xl font-bold text-gray-800">{{ stat.valeur }}</p>
      <p class="text-xs text-gray-400">{{ stat.sousTitre }}</p>
    </div>
  </div>
</template>

<script setup>
const stats = [
  { label: 'Surface', valeur: '2 ha', sousTitre: '12 parcelles' },
  { label: 'Cultures', valeur: '24', sousTitre: 'variétés actives' },
  { label: 'Serres', valeur: '3', sousTitre: '850 m² couverts' },
  { label: 'Rappels', valeur: '5', sousTitre: 'cette semaine' }
]
</script>