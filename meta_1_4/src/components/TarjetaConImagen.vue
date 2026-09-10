<template>
  <v-card class="mx-auto" max-width="400">
    <v-img :src="imageUrl" height="200" cover></v-img>
    <v-card-title>{{ title }}</v-card-title>
    <v-card-subtitle>Foto por: {{ author }}</v-card-subtitle>
    <v-card-text>{{ description }}</v-card-text>
  </v-card>
</template>

<script setup>
defineProps({
  imageUrl: {
    type: String,
    required: true
  },
  title: {
    type: String,
    default: 'Sin título'
  },
  description: {
    type: String,
    default: ''
  },
  author: {
    type: String,
    default: 'Autor desconocido'
  }
})
</script>