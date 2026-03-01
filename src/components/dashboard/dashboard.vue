<template>
  <div class="min-h-screen bg-gray-50">
    <!-- En-tête -->
    <div class="bg-gradient-to-r from-green-600 to-green-500 text-white px-4 py-6 fixed top-0 left-0 right-0 z-10 shadow-lg">
      <div class="flex justify-between items-center">
        <h1 class="text-2xl font-bold">🌱 MaraîcherBio</h1>
        <div class="flex items-center space-x-4">
          <span class="text-lg">☀️ 14°C</span>
        </div>
      </div>
      <p class="text-green-100 text-sm mt-1">Saint-Malo · Bretagne</p>
    </div>

    <!-- Contenu principal -->
    <div class="pt-24 pb-20 px-4">
      <!-- Cartes statistiques -->
      <div class="grid grid-cols-2 gap-3 mb-6">
        <div class="bg-white rounded-xl shadow-sm p-4">
          <p class="text-gray-500 text-xs">Surface</p>
          <p class="text-2xl font-bold text-gray-800">2 ha</p>
          <p class="text-xs text-gray-400">12 parcelles</p>
        </div>
        <div class="bg-white rounded-xl shadow-sm p-4">
          <p class="text-gray-500 text-xs">Cultures</p>
          <p class="text-2xl font-bold text-gray-800">24</p>
          <p class="text-xs text-gray-400">variétés actives</p>
        </div>
        <div class="bg-white rounded-xl shadow-sm p-4">
          <p class="text-gray-500 text-xs">Serres</p>
          <p class="text-2xl font-bold text-gray-800">3</p>
          <p class="text-xs text-gray-400">850 m² couverts</p>
        </div>
        <div class="bg-white rounded-xl shadow-sm p-4">
          <p class="text-gray-500 text-xs">Rappels</p>
          <p class="text-2xl font-bold text-gray-800">5</p>
          <p class="text-xs text-gray-400">cette semaine</p>
        </div>
      </div>

      <!-- Section Rappels urgents -->
      <div class="mb-6">
        <h2 class="text-lg font-semibold text-gray-800 mb-3">Rappels urgents</h2>
        <div class="space-y-3">
          <!-- Rappel 1 -->
          <div class="bg-white rounded-xl shadow-sm p-4 border-l-4 border-red-500">
            <div class="flex justify-between items-start">
              <div>
                <p class="font-medium text-gray-800">💧 Arrosage – Serre A</p>
                <p class="text-xs text-gray-500 mt-1">Aujourd'hui · Sol sec</p>
              </div>
              <span class="bg-red-100 text-red-600 text-xs px-2 py-1 rounded-full">Urgent</span>
            </div>
          </div>

          <!-- Rappel 2 -->
          <div class="bg-white rounded-xl shadow-sm p-4 border-l-4 border-yellow-500">
            <div class="flex justify-between items-start">
              <div>
                <p class="font-medium text-gray-800">🌱 Semis tomates Roma</p>
                <p class="text-xs text-gray-500 mt-1">Dans 3 jours · 3 mars</p>
              </div>
              <span class="bg-yellow-100 text-yellow-600 text-xs px-2 py-1 rounded-full">Semis</span>
            </div>
          </div>

          <!-- Rappel 3 -->
          <div class="bg-white rounded-xl shadow-sm p-4">
            <div class="flex justify-between items-start">
              <div>
                <p class="font-medium text-gray-800">✂️ Taille haricots verts</p>
                <p class="text-xs text-gray-500 mt-1">5 mars</p>
              </div>
              <span class="bg-blue-100 text-blue-600 text-xs px-2 py-1 rounded-full">Entretien</span>
            </div>
          </div>

          <!-- Rappel 4 -->
          <div class="bg-white rounded-xl shadow-sm p-4">
            <div class="flex justify-between items-start">
              <div>
                <p class="font-medium text-gray-800">🥕 Récolte carottes Nantaise</p>
                <p class="text-xs text-gray-500 mt-1">10 mars</p>
              </div>
              <span class="bg-purple-100 text-purple-600 text-xs px-2 py-1 rounded-full">Récolte</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Météo rapide -->
      <div class="mb-6">
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
            <div>
              <p class="text-gray-500">Auj.</p>
              <p class="font-medium">☀️ 14°</p>
            </div>
            <div>
              <p class="text-gray-500">Dim</p>
              <p class="font-medium">⛅ 12°</p>
            </div>
            <div>
              <p class="text-gray-500">Lun</p>
              <p class="font-medium">🌧 10°</p>
            </div>
          </div>
        </div>
      </div>

      <!-- Conseils maraîchage -->
      <div class="mb-6">
        <h2 class="text-lg font-semibold text-gray-800 mb-3">🌱 Conseils maraîchage</h2>
        <div class="space-y-2">
          <div class="bg-yellow-50 border-l-4 border-yellow-500 p-3 rounded-r-lg">
            <p class="text-sm text-yellow-800">💧 Arrosage recommandé (sol sec, peu de pluie prévue)</p>
          </div>
          <div class="bg-green-50 border-l-4 border-green-500 p-3 rounded-r-lg">
            <p class="text-sm text-green-800">🌱 Conditions favorables aux semis sous abri</p>
          </div>
          <div class="bg-blue-50 border-l-4 border-blue-500 p-3 rounded-r-lg">
            <p class="text-sm text-blue-800">❄️ Pas de risque de gel cette semaine</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Barre de navigation mobile -->
    <div class="fixed bottom-0 left-0 right-0 bg-white border-t border-gray-200 px-6 py-2 flex justify-around items-center text-xs text-gray-500">
      <div class="flex flex-col items-center text-green-600">
        <span class="text-xl mb-1">🏠</span>
        <span>Accueil</span>
      </div>
      <div class="flex flex-col items-center">
        <span class="text-xl mb-1">🌦️</span>
        <span>Météo</span>
      </div>
      <div class="flex flex-col items-center">
        <span class="text-xl mb-1">📅</span>
        <span>Calendrier</span>
      </div>
      <div class="flex flex-col items-center">
        <span class="text-xl mb-1">🧑‍🌾</span>
        <span>Parcelles</span>
      </div>
      <div class="flex flex-col items-center">
        <span class="text-xl mb-1">🌱</span>
        <span>Semences</span>
      </div>
    </div>
  </div>
</template>

<script setup>
// Plus tard on rendra les données dynamiques
</script>