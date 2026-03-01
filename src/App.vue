<template>
  <div class="min-h-screen bg-green-50 p-8">
    <h1 class="text-3xl font-bold text-green-800 mb-6">
      🌱 Mon Jardin Bio - Catalogue des semences
    </h1>
    
    <SemencesList />
  </div>
</template>

<script setup>
import SemencesList from './components/semences/SemencesList.vue'
</script>