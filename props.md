
⭐ Props (Comunicación Padre → Hijo)
Las props permiten que un componente padre envíe datos a un hijo.
¿Cuándo usar props?
Para configurar un componente.
Para mostrar información dinámica.
Para listas de componentes (tarjetas, tablas, items, etc.)
✔ Ejemplo 1 – Mostrar un título dinámico
<!-- Titulo.vue -->
<script setup>
defineProps({ texto: String });
</script>
​
<template>
  <h1>{{ texto }}</h1>
</template>
Uso:
<Titulo texto="Bienvenido a mi app" />
✔ Ejemplo 2 – Componente de producto
<!-- Producto.vue -->
<script setup>
defineProps({
  nombre: String,
  precio: Number,
});
</script>
​
<template>
  <p>{{ nombre }} - ${{ precio }}</p>
</template>
Uso:
<Producto nombre="Laptop" precio="12000" />