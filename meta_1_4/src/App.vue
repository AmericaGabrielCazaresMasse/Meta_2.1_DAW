<script setup>
import AppFooter from './components/AppFooter.vue'
import AppHeader from './components/AppHeader.vue'
</script>

<template>
  <v-app>
    <AppHeader />
    <v-main>
      <v-container>
        <p>Contenido de prueba</p>
      </v-container>
    </v-main>
    <AppFooter />
  </v-app>
</template>