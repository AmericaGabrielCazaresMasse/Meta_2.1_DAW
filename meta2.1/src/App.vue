<script setup>
import { onMounted } from "vue";
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
 
onMounted(() => {
  document.title = "Mi Portafolio Fotográfico";
});
</script>

<template>
  <v-app>
    <AppHeader />
 
    <router-view />
 
    <AppFooter />
  </v-app>
</template>
 