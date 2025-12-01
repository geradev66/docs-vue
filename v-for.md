⭐ v-for
Itera listas, objetos o rangos.

Ejemplo 1 – Lista simple
<li v-for="(tarea, i) in tareas" :key="i">{{ tarea }}</li>

✔ Ejemplo 2 – Renderizar componentes con props
<Producto
  v-for="p in productos"
  :key="p.id"
  :nombre="p.nombre"
  :precio="p.precio"
/>