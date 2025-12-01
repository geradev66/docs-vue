😄 provide() / inject() — Compartir datos globales entre componentes
¿Cuándo usarlo?
Temas (dark/light)
Configuración global
Usuario logueado
Evitar pasar props por muchos niveles
✔ Ejemplo 1 – Tema global
✔ Ejemplo 2 – Idioma global
Sistema Global de Modo Oscuro (Dark Mode)
Este ejemplo enseña:
Proveer un estado global.
Aplicar el tema al <body>.
Cambiar el tema desde cualquier componente.
🟦 1. Proveedor de tema
App.vue
<script setup>
import { ref, watch, provide } from "vue";
​
const modoOscuro = ref(false);
​
function toggleTema() {
  modoOscuro.value = !modoOscuro.value;
}
​
// Aplicar el tema al <body>
watch(modoOscuro, (nuevoValor) => {
  if (nuevoValor) {
    document.body.classList.add("dark");
  } else {
    document.body.classList.remove("dark");
  }
});
​
// Proveer estado y función global
provide("modoOscuro", modoOscuro);
provide("toggleTema", toggleTema);
</script>
​
<template>
  <div>
    <h1>Sistema de Tema Global</h1>
    <BotonTema />
    <Contenido />
  </div>
</template>
🟦 2. Botón para cambiar tema desde cualquier componente
BotonTema.vue
<script setup>
import { inject, computed } from "vue";
​
const modoOscuro = inject("modoOscuro");
const toggleTema = inject("toggleTema");
​
const texto = computed(() =>
  modoOscuro.value ? "Cambiar a modo claro" : "Cambiar a modo oscuro"
);
</script>
​
<template>
  <button @click="toggleTema">
    {{ texto }}
  </button>
</template>
🟦 3. Componente que cambia estilo según el tema
Contenido.vue
<script setup>
import { inject, computed } from "vue";
​
const modoOscuro = inject("modoOscuro");
​
const claseTema = computed(() =>
  modoOscuro.value ? "caja dark" : "caja light"
);
</script>
​
<template>
  <div :class="claseTema">
    Este es un componente que cambia según el tema.
  </div>
</template>
​
<style>
.caja {
  padding: 20px;
  margin-top: 20px;
  border-radius: 10px;
}
.light {
  background: #f0f0f0;
  color: #222;
}
.dark {
  background: #222;
  color: #fff;
}
</style>