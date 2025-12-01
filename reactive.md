reactive() convierte objetos, arrays o mapas en reactivos sin usar .value.
¿Cuándo usarlo?
Formularios complejos
Modelos de datos grandes
Objetos anidados

✔ Ejemplo 1 – Formulario completo
<script setup>
import { reactive } from "vue";

const form = reactive({
  nombre: "",
  email: "",
  edad: null,
  direccion: {
    calle: "",
    ciudad: ""
  }
});
</script>

<template>
  <input v-model="form.nombre" placeholder="Nombre">
  <input v-model="form.email" placeholder="Email">
  <input v-model="form.direccion.calle" placeholder="Calle">

  <pre>{{ form }}</pre>
</template>

✔ Ejemplo 2 – Carrito de compras
<script setup>
import { reactive } from "vue";

const carrito = reactive({
  items: [],
  total: 0
});

function agregarProducto(p) {
  carrito.items.push(p);
  carrito.total += p.precio;
}
</script>

<template>
  <button @click="agregarProducto({ nombre: 'Laptop', precio: 15000 })">
    Agregar Laptop
  </button>

  <ul>
    <li v-for="i in carrito.items">{{ i.nombre }} - ${{ i.precio }}</li>
  </ul>

  <h3>Total: {{ carrito.total }}</h3>
</template>