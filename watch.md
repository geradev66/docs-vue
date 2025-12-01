😄 watch() — Observar cambios específicos
watch() — Observar cambios específicos
watch() escucha cambios de uno o varios valores reactivos.
¿Cuándo usar watch()?
Llamar una API cuando un valor cambia
Guardar cosas en localStorage
Validar formularios
Reaccionar a cambios “fuera de la UI”
✔ Ejemplo 1 – Guardar automáticamente en localStorage
<script setup>
import { ref, watch } from "vue";
​
const texto = ref("");
​
watch(texto, (nuevo) => {
  localStorage.setItem("nota", nuevo);
});
</script>
​
<template>
  <textarea v-model="texto"></textarea>
</template>
✔ Ejemplo 2 – Validación de email
<script setup>
import { ref, watch } from "vue";
​
const email = ref("");
const valido = ref(false);
​
watch(email, (v) => {
  valido.value = /^[\w-.]+@[\w-]+\.[a-z]{2,4}$/i.test(v);
});
</script>
​
<template>
  <input v-model="email" placeholder="correo@mail.com">
  <p v-if="valido">✔ Email válido</p>
  <p v-else>❌ Email incorrecto</p>
</template>






 😄 watchEffect() — Se ejecuta automáticamente
Se ejecuta cada vez que cualquier variable usada dentro cambie.
¿Cuándo usarlo?
Para depuración
Lógica automática sin declarar qué observar
Efectos secundarios simples

✔ Ejemplo 1 – Registrar cambios de cualquier variable
<script setup>
import { ref, watchEffect } from "vue";

const x = ref(0);
const y = ref(0);

watchEffect(() => {
  console.log(`Nueva posición: (${x.value}, ${y.value})`);
});
</script>

✔ Ejemplo 2 – Cargar datos según estado
<script setup>
import { ref, watchEffect } from "vue";

const id = ref(1);
const data = ref(null);

watchEffect(async () => {
  data.value = await fetch(`https://jsonplaceholder.typicode.com/posts/${id.value}`)
    .then(r => r.json());
});
</script>