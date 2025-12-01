⭐V-model
Crea un enlace bidireccional entre una variable y el input.
¿Cuándo usarlo?
Formularios
Filtros en tablas
Inputs reactivos
Configuración de componentes
✔ Ejemplo 1 – Campo de texto

<input v-model="nombre" placeholder="Nombre">
<p>Escribiste: {{ nombre }}</p>
✔ Ejemplo 2 – Checkbox multiple
<script setup>
import { ref } from "vue";
const seleccionados = ref([]);
</script>
​
<template>
  <label><input type="checkbox" value="Vue" v-model="seleccionados"> Vue</label>
  <label><input type="checkbox" value="React" v-model="seleccionados"> React</label>
​
  <p>Seleccionaste: {{ seleccionados }}</p>
</template>