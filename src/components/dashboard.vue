<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Header fixe -->
    <Header />

    <!-- Navigation par onglets -->
    <NavTabs v-model="ongletActif" :tabs="onglets" />

    <!-- Contenu principal -->
    <main class="pt-36 pb-20 px-4">
      <div v-show="ongletActif === 'accueil'" class="space-y-6">
        <StatsCards />
        <RappelsUrgents />
        <MeteoRapide />
        <ConseilsMaraichage />
      </div>

      <div v-show="ongletActif === 'meteo'">
        <MeteoDetail />
      </div>

      <div v-show="ongletActif === 'calendrier'">
        <Calendrier />
      </div>

      <div v-show="ongletActif === 'parcelles'">
        <Parcelles />
      </div>

      <div v-show="ongletActif === 'plantes'">
        <Plantes />
      </div>

      <div v-show="ongletActif === 'scanner'">
        <Scanner />
      </div>

      <div v-show="ongletActif === 'compta'">
        <Compta />
      </div>
    </main>

    <!-- Barre de navigation mobile -->
    <NavBottom v-model="ongletActif" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Header from './Header.vue'
import NavTabs from './NavTabs.vue'
import NavBottom from './NavBottom.vue'
import StatsCards from './StatsCards.vue'
import RappelsUrgents from './RappelsUrgents.vue'
import MeteoRapide from './MeteoRapide.vue'
import ConseilsMaraichage from './ConseilsMaraichage.vue'
import MeteoDetail from '@/components/meteo/MeteoDetail.vue'
import Calendrier from '@/components/calendrier/Calendrier.vue'
import Parcelles from '@/components/parcelles/Parcelles.vue'
import Plantes from '@/components/plantes/Plantes.vue'
import Scanner from '@/components/scanner/Scanner.vue'
import Compta from '@/components/compta/Compta.vue'

const ongletActif = ref('accueil')
const onglets = [
  { id: 'accueil', label: '🌱 Accueil' },
  { id: 'meteo', label: '🌤 Météo' },
  { id: 'calendrier', label: '📅 Calendrier' },
  { id: 'parcelles', label: '🗺 Parcelles' },
  { id: 'plantes', label: '🌿 Plantes' },
  { id: 'scanner', label: '📷 Scanner' },
  { id: 'compta', label: '📊 Compta' }
]
</script>