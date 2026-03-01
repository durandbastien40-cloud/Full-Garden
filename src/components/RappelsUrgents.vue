<template>
  <div>
    <h2 class="text-lg font-semibold text-gray-800 mb-3">Rappels urgents</h2>
    <div class="space-y-3">
      <div
        v-for="rappel in rappels"
        :key="rappel.titre"
        class="bg-white rounded-xl shadow-sm p-4"
        :class="{
          'border-l-4 border-red-500': rappel.urgent,
          'border-l-4 border-yellow-500': rappel.type === 'Semis'
        }"
      >
        <div class="flex justify-between items-start">
          <div>
            <p class="font-medium text-gray-800">{{ rappel.icone }} {{ rappel.titre }}</p>
            <p class="text-xs text-gray-500 mt-1">{{ rappel.date }}</p>
          </div>
          <span
            class="text-xs px-2 py-1 rounded-full"
            :class="{
              'bg-red-100 text-red-600': rappel.urgent,
              'bg-yellow-100 text-yellow-600': rappel.type === 'Semis',
              'bg-blue-100 text-blue-600': rappel.type === 'Entretien',
              'bg-purple-100 text-purple-600': rappel.type === 'Récolte'
            }"
          >
            {{ rappel.type }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const rappels = [
  { icone: '💧', titre: 'Arrosage — Serre A', date: 'Aujourd\'hui · Sol sec', type: 'Urgent', urgent: true },
  { icone: '🌱', titre: 'Semis tomates Roma', date: 'Dans 3 jours · 3 mars', type: 'Semis', urgent: false },
  { icone: '✂️', titre: 'Taille haricots verts', date: '5 mars', type: 'Entretien', urgent: false },
  { icone: '🥕', titre: 'Récolte carottes Nantaise', date: '10 mars', type: 'Récolte', urgent: false }
]
</script>