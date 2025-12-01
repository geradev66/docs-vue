⭐ Emit (Comunicación Hijo → Padre)
Permite al hijo enviar eventos personalizados al padre.
¿Cuándo usar emits?
Cuando el hijo necesita informar al padre.
Formularios, botones, inputs personalizados.
✔ Ejemplo 1 – Botón que envía evento
<!-- Hijo.vue -->
<script setup>
const emit = defineEmits(["accion"]);
</script>
​
<template>
  <button @click="emit('accion')">Ejecutar</button>
</template>
Padre:
<Hijo @accion="hacerAlgo" />
✔ Ejemplo 2 – Input personalizado

<!-- InputTexto.vue -->
<script setup>
const emit = defineEmits(["update:modelValue"]);
defineProps(["modelValue"]);
​
function escribir(e) {
  emit("update:modelValue", e.target.value);
}
</script>
​
<template>
  <input :value="modelValue" @input="escribir">
</template>
Uso:
<InputTexto v-model="nombre" />