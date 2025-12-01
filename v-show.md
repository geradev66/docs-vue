⭐ v-show
Oculta el elemento con display: none, pero sigue en el DOM.
¿Cuándo usarlo?
Mostrar/ocultar muy seguido (mejor rendimiento que v-if).
Tabs, paneles, modales.

✔ Ejemplo 1 – Panel visible

<div v-show="visible">
  Este panel aparece y desaparece rápido.
</div>

✔ Ejemplo 2 – Botón cargando
<button>
  <span v-show="!cargando">Enviar</span>
  <span v-show="cargando">Cargando...</span>
</button>