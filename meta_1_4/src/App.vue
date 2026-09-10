<script setup>
import TarjetaConImagen from './components/TarjetaConImagen.vue'
</script>

<template>
  <v-app>
    <v-main>
      <TarjetaConImagen
        image-url="https://picsum.photos/id/10/300/200"
        title="Tarjeta de Prueba"
        description="Probando el componente"
        author="Autor de prueba"
      />
    </v-main>
  </v-app>
</template>