<script setup>
import { ref } from 'vue'
import TarjetaConImagen from '@/components/TarjetaConImagen.vue'
import TablaDeDatos from '@/components/TablaDeDatos.vue'

const tarjeta1 = ref({
  imageUrl: 'https://picsum.photos/id/10/300/200',
  title: 'Fotografía 1',
  description: 'Imagen obtenida desde la API de Picsum',
  author: 'Cargando...'
})

const tarjeta2 = ref({
  imageUrl: 'https://picsum.photos/id/20/300/200',
  title: 'Fotografía 2',
  description: 'Imagen obtenida desde la API de Picsum',
  author: 'Cargando...'
})

const cargando = ref(false)
const error = ref(null)

async function obtenerDosImagenesAleatorias() {
  const respuesta = await fetch('https://picsum.photos/v2/list?page=1&limit=100')

  if (!respuesta.ok) {
    throw new Error('No se pudo conectar con la API de Picsum')
  }

  const listaImagenes = await respuesta.json()

  if (!Array.isArray(listaImagenes) || listaImagenes.length < 2) {
    throw new Error('La API no devolvió suficientes imágenes')
  }

  const indice1 = Math.floor(Math.random() * listaImagenes.length)

  let indice2
  do {
    indice2 = Math.floor(Math.random() * listaImagenes.length)
  } while (indice2 === indice1)

  return [listaImagenes[indice1], listaImagenes[indice2]]
}

async function actualizarImagenes() {
  // Evita disparar peticiones en paralelo
  if (cargando.value) return

  cargando.value = true
  error.value = null

  try {
    const [img1, img2] = await obtenerDosImagenesAleatorias()

    tarjeta1.value = {
      imageUrl: `https://picsum.photos/id/${img1.id}/300/200`,
      title: 'Fotografía 1',
      description: 'Imagen obtenida desde la API de Picsum',
      author: img1.author
    }

    tarjeta2.value = {
      imageUrl: `https://picsum.photos/id/${img2.id}/300/200`,
      title: 'Fotografía 2',
      description: 'Imagen obtenida desde la API de Picsum',
      author: img2.author
    }
  } catch (e) {
    error.value = 'Ocurrió un error al obtener las imágenes. Intenta de nuevo.'
    console.error(e)
  } finally {
    cargando.value = false
  }
}
</script>

<template>
  <v-main>
    <v-container>
      <v-row justify="center">
        <v-col cols="12" md="6">
          <TarjetaConImagen
            :image-url="tarjeta1.imageUrl"
            :title="tarjeta1.title"
            :description="tarjeta1.description"
            :author="tarjeta1.author"
          />
        </v-col>
        <v-col cols="12" md="6">
          <TarjetaConImagen
            :image-url="tarjeta2.imageUrl"
            :title="tarjeta2.title"
            :description="tarjeta2.description"
            :author="tarjeta2.author"
          />
        </v-col>
      </v-row>

      <!-- Botón de actualización -->
      <v-row justify="center" class="my-4">
        <v-col cols="12" class="text-center">
          <v-btn
            color="#B39DDB"
            :loading="cargando"
            :disabled="cargando"
            @click="actualizarImagenes"
          >
            Actualizar Imágenes
          </v-btn>
        </v-col>
      </v-row>

      <!-- Mensaje de error -->
      <v-row v-if="error" justify="center">
        <v-col cols="12" md="8">
          <v-alert type="error" closable @click:close="error = null">
            {{ error }}
          </v-alert>
        </v-col>
      </v-row>

      <!-- Tabla de datos -->
      <v-row justify="center" class="mt-6">
        <v-col cols="12">
          <TablaDeDatos />
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>