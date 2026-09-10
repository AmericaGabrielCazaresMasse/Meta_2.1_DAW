<script setup>
import AppFooter from './components/AppFooter.vue'
import AppHeader from './components/AppHeader.vue'
import TablaDeDatos from './components/TablaDeDatos.vue'
</script>

<template>
  <v-app>
    <AppHeader />
    <v-main>
      <v-container>
        <TablaDeDatos />
      </v-container>
    </v-main>
    <AppFooter />
  </v-app>
</template>
