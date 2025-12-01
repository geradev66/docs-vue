🍍
PINIA — Manejo global de estado
Pinia es el store oficial de Vue.
¿Cuándo usar Pinia?
Autenticación (usuario global)
Carrito de compras
Notificaciones globales
Preferencias
3.1 Instalación
3.2 Configuración
✔ Ejemplo 1 – Store de usuario
Uso:
✔ Ejemplo 2 – Carrito de compras
Crear un store con Pinia — Composition API Store Syntax (setup store)
Este store consumirá una API Django:
📁 src/stores/userStore.js
Usar el store Pinia desde un componente (Composition API)
Ejemplo de una tabla de usuarios:
📁 src/components/UserList.vue



<script setup>
import { onMounted } from "vue";
import { useUserStore } from "../stores/userStore";
​
const userStore = useUserStore();
​
onMounted(() => {
  userStore.fetchUsers();
});
</script>
​
<template>
  <div>
    <h2>Usuarios</h2>
​
    <div v-if="userStore.loading">Cargando...</div>
    <div v-if="userStore.error">{{ userStore.error }}</div>
​
    <table v-if="!userStore.loading">
      <thead>
        <tr>
          <th>ID</th>
          <th>Nombre</th>
          <th>Email</th>
        </tr>
      </thead>
​
      <tbody>
        <tr v-for="u in userStore.users" :key="u.id">
          <td>{{ u.id }}</td>
          <td>{{ u.name }}</td>
          <td>{{ u.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>


🟦 4) Formulario para crear usuario
📁 src/components/UserCreate.vue
<script setup>
import { ref } from "vue";
import { useUserStore } from "../stores/userStore";
​
const store = useUserStore();
​
const form = ref({
  name: "",
  email: "",
  password: "",
});
​
function submit() {
  store.createUser(form.value);
}
</script>
​
<template>
  <div>
    <h2>Crear usuario</h2>
​
    <form @submit.prevent="submit">
      <input v-model="form.name" placeholder="Nombre" />
      <input v-model="form.email" placeholder="Email" />
      <input v-model="form.password" placeholder="Contraseña" type="password" />
​
      <button type="submit">Guardar</button>
    </form>
​
    <p v-if="store.loading">Guardando...</p>
    <p v-if="store.error">{{ store.error }}</p>
  </div>
</template>