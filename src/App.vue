<template>
  <div class="min-h-screen bg-green-50 p-8">
    <h1 class="text-3xl font-bold text-green-800 mb-6">
      🌱 Mon Jardin Bio
    </h1>
    
    <MeteoWidget />
  </div>
</template>

<script setup>
import MeteoWidget from './components/meteo/MeteoWidget.vue'
</script>