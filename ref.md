ref() — Valores primitivos reactivos
ref() crea una caja reactiva que envuelve un valor.
Siempre accedes a su valor con .value.
¿Cuándo usarlo?
Valores simples: número, string, boolean
Inputs de formularios
Estados que cambian con eventos

✔ Ejemplo 1 – Temporizador (start / stop)
<script setup>
import { ref } from "vue";
​
const tiempo = ref(0);
let intervalo;
​
function iniciar() {
  intervalo = setInterval(() => tiempo.value++, 1000);
}
​
function detener() {
  clearInterval(intervalo);
}
</script>
​
<template>
  <p>Segundos: {{ tiempo }}</p>
  <button @click="iniciar">Iniciar</button>
  <button @click="detener">Detener</button>
</template>

✔ Ejemplo 2 – Sistema de likes
<script setup>
import { ref } from "vue";
​
const likes = ref(120);
const activo = ref(false);
​
function toggle() {
  activo.value = !activo.value;
  activo.value ? likes.value++ : likes.value--;
}
</script>
​
<template>
  <button @click="toggle">
    👍 {{ likes }} ({{ activo ? "Te gusta" : "Sin like" }})
  </button>
</template>