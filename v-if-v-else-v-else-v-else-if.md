⭐ v-if / v-else-if / v-else
Muestra u oculta elementos eliminándolos del DOM.
¿Cuándo usarlo?
Interfaces donde un elemento depende de una condición.
Cambios que no se hacen frecuentemente (porque es costoso renderizar).

✔ Ejemplo 1 – Mostrar mensaje según la edad
<p v-if="edad >= 18">Adulto</p>
<p v-else>Menor</p>
✔ Ejemplo 2 – Autenticación
<div v-if="usuario">
  Bienvenido, {{ usuario.nombre }}
</div>
<div v-else>
  Debes iniciar sesión
</div>