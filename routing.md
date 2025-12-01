😎 ROUTING – Vue Router 4
Instalación
npm install vue-router
Configuración básica
// router.js
import { createRouter, createWebHistory } from "vue-router";
import Home from "./views/Home.vue";
import About from "./views/About.vue";
​
export default createRouter({
  history: createWebHistory(),
  routes: [
    { path: "/", component: Home },
    { path: "/about", component: About }
  ]
});
Y en main.js:
import router from "./router";
app.use(router);
Ejemplo 1 – Navegación con <router-link>
<router-link to="/">Inicio</router-link>
<router-link to="/about">Acerca de</router-link>
​
<router-view />
✔ Ejemplo 2 – Parámetros dinámicos
{ path: "/user/:id", component: User }
<script setup>
import { useRoute } from "vue-router";
const route = useRoute();
const id = route.params.id;
</script>
​
<template>
  <p>Usuario: {{ id }}</p>
</template>