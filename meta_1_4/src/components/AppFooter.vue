<script setup>
import { ref } from 'vue'

const fechaActual = ref(new Date().toLocaleDateString('es-MX', {
  year: 'numeric', month: 'long', day: 'numeric'
}))
</script>

<template>
  <v-footer color="#B39DDB" class="text-center d-flex flex-column">
    <v-container>
      <v-row justify="center">
        <v-col cols="12" sm="4">
          <strong>America Gabriel Cazares Masse</strong>
        </v-col>
        <v-col cols="12" sm="4">
          Matrícula: 01190103
        </v-col>
        <v-col cols="12" sm="4">
          {{ fechaActual }}
        </v-col>
      </v-row>
      <v-row justify="center">
        <v-col cols="12">
          © 2026 Mi Portafolio. Todos los derechos reservados.
        </v-col>
      </v-row>
    </v-container>
  </v-footer>
</template>