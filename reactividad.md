
⭐ Reactividad
​
La reactividad es el corazón de Vue.
Consiste en que Vue detecta los cambios de los datos y actualiza la interfaz automáticamente, sin que tú tengas que manipular el DOM manualmente.
¿Cuándo usar reactividad?
Cuando un valor cambia con el tiempo.
Cuando necesitas sincronizar variables con el DOM.
Formularios, contadores, estados, listas, filtros, etc.

✔ Ejemplo 1 – Contador reactivo básico
<script setup>
import { ref } from "vue";
​
const contador = ref(0);
​
function incrementar() {
  contador.value++;
}
</script>
​
<template>
  <p>Valor: {{ contador }}</p>
  <button @click="incrementar">+</button>
</template>
Qué ocurre:
Cada vez que .value cambia, Vue vuelve a renderizar automáticamente.
✔ Ejemplo 2 – Cambios que actualizan contenido dinámico
<script setup>
import { ref } from "vue";
​
const nombre = ref("Gerardo");
const mensaje = ref("");
​
function actualizarMensaje() {
  mensaje.value = `Hola ${nombre.value}, bienvenido 👋`;
}
</script>
​
<template>
  <input v-model="nombre" placeholder="Escribe tu nombre">
  <button @click="actualizarMensaje">Actualizar saludo</button>
  <p>{{ mensaje }}</p>
</template>
​
