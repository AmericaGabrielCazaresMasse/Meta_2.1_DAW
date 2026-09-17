<script setup>
const habilidades = [
  { habilidad: 'Ensamblador', nivel: 'Básico', proyectos: 1 },
  { habilidad: 'Python', nivel: 'Básico', proyectos: 1 },
  { habilidad: 'HTML/CSS', nivel: 'Básico', proyectos: 2 },
  { habilidad: 'Git', nivel: 'Básico', proyectos: 2 },
]
</script>

<template>
  <v-table>
    <thead>
      <tr>
        <th>Habilidad</th>
        <th>Nivel</th>
        <th>Proyectos realizados</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in habilidades" :key="item.habilidad">
        <td>{{ item.habilidad }}</td>
        <td>{{ item.nivel }}</td>
        <td>{{ item.proyectos }}</td>
      </tr>
    </tbody>
  </v-table>
</template>