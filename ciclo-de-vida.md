Ciclo de vida
Hooks más usados:
Hook
Cuándo se ejecuta
onMounted
Cuando el componente ya está en el DOM (muy usado en fetch)
onUpdated
Cuando cambia algo reactivo dentro
onUnmounted
Antes de destruir el componente
onBeforeMount
Antes de montar
onBeforeUpdate
Antes de actualizar


✔ Ejemplo 1 – Cargar datos al montar
<script setup>
import { onMounted, ref } from "vue";
​
const posts = ref([]);
​
onMounted(async () => {
  posts.value = await fetch("https://jsonplaceholder.typicode.com/posts").then(r => r.json());
});
</script>
✔ Ejemplo 2 – Limpiar intervalos
<script setup>
import { ref, onMounted, onUnmounted } from "vue";
​
const tiempo = ref(0);
let intervalo;
​
onMounted(() => {
  intervalo = setInterval(() => tiempo.value++, 1000);
});
​
onUnmounted(() => {
  clearInterval(intervalo);
});
</script>