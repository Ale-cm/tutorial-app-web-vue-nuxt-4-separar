<template>
	<div>
	<h2>Catalogo</h2>
  <ul>
    <li
      v-for="producto in catalogo"
      :key="producto.id">
      {{ producto.dsc }} - {{ producto.precio }}

      <button
        @click="agregarAlCarrito(producto)">
        Agregar al carrito
      </button>

     </li>
  </ul>

	<!-- XXX: lo que ya tiene el carrito deberia ir en otro componente -->
	<h2>Carrito</h2>
  <ul>
    <li
      v-for="(producto, posicion) in carrito"
      >
      {{ producto.dsc }}

      <button
        @click="quitarDelCarrito(posicion)">
        Quitar
      </button>
    </li>
  </ul>
	</div>
</template>

<script>
var ProductosDePrueba= [
  {id: 1, dsc: "hojas A4", precio: 101.00},
  {id: 21, dsc: "marcadores", precio: 21.05},
]; //XXX: mover a store y api

export default {
  name: "PagComprar",
  data () {return{ //U: funcion, devuelve clave-valor con datos que uso
    catalogo: ProductosDePrueba,
		carrito: [],	
  } },
  computed: {}, //U: propiedades que se calculan en base a otras
	methods: { //U: acciones de botones, etc.
		agregarAlCarrito: function (que) {
			console.log("carrito, agregar",que.dsc);
			this.carrito.push(que);
			console.log("carrito agregado",que.dsc, JSON.stringify(this.carrito,1) );
		},
		quitarDelCarrito: function (posicion) {
			console.log("carrito, quitar",posicion);
			var que= this.carrito[posicion];
			this.carrito.splice(posicion,1); //A: eliminar el item en esa posicion
			console.log("carrito, quitado",posicion, que, JSON.stringify(this.carrito,1) );
		}
	},
  created () { console.log("created",this); } //U: para inicializar el componente
}
</script>


