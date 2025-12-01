😄 computed() — Propiedades derivadas
computed() crea valores basados en otros valores reactivos.
Se recalculan solo cuando es necesario (caché).
¿Cuándo usarlo?
Mostrar valores calculados
Filtros
Ordenamientos
Estados derivados (activo/inactivo, completado/no completado)
✔ Ejemplo 1 – Nombre completo
<script setup>
import { ref, computed } from "vue";
​
const nombre = ref("Gerardo");
const apellido = ref("Ponce");
​
const nombreCompleto = computed(() => {
  return `${nombre.value} ${apellido.value}`;
});
</script>
​
<template>
  <p>{{ nombreCompleto }}</p>
</template>
✔ Ejemplo 2 – Filtrar lista
<script setup>
import { ref, computed } from "vue";
​
const busqueda = ref("");
const productos = ref(["Laptop", "Mouse", "Teclado", "Monitor"]);
​
const filtrados = computed(() => {
  return productos.value.filter(p =>
    p.toLowerCase().includes(busqueda.value.toLowerCase())
  );
});
</script>
​
<template>
  <input v-model="busqueda" placeholder="Buscar...">
​
  <p>Resultados:</p>
  <ul>
    <li v-for="p in filtrados" :key="p">{{ p }}</li>
  </ul>
</template>