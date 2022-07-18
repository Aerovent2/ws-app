<template>
<div class="container px-4 py-5"> 

  <ul class="list-group">
    <div v-for="(producto, index) in itemsCarrito" :key="index">
     <li class="list-group-item"><span>{{producto.title}}</span><strong class="p-3">${{producto.price}} </strong> 
     <p >Cantidad</p><button class="btn btn-secondary" @click="producto.cantidad= producto.cantidad - 1, cantidadItems(producto.cantidad, producto.id)">-</button><label >{{producto.cantidad}}</label> <button class="btn btn-primary" @click="producto.cantidad= producto.cantidad + 1, cantidadItems(producto.cantidad, producto.id)">+</button>
      <button class="btn btn-warning mx-3" @click="quitarItem(producto.id)">x</button>
      <p>Subtotal ${{producto.price * producto.cantidad}} </p>
     </li>
      
    </div>

    <p>Total ${{sumaTotal}}</p>
  </ul>

  <button @click="volver()" class="btn btn-primary">Volver a Productos</button>
</div>   
</template>

<script>
export default {
  name: 'CarritoCompras',
  props:['itemsParaelCarrito'],
  data(){
    return {
      itemsCarrito : this.itemsParaelCarrito,
      total:0 }
    },
  methods:{
    volver(){
      
      this.$emit('emitCarrito', false)
    },
    quitarItem(id){
      console.log(id)
      let carritoActualizado = this.itemsCarrito.filter(item => item.id !== id)
      this.itemsCarrito = carritoActualizado
    },
    cantidadItems(cantidad, id){
      let encontrado = this.itemsCarrito.find(item => item.id === id)
      let index = this.itemsCarrito.indexOf(encontrado)
      this.itemsCarrito[index].cantidad = cantidad
              
    }

  },
  computed: {
    sumaTotal(){
      
      let cantidad = 0
      let subtotal=0
      this.itemsCarrito.forEach(item =>{
        subtotal= item.cantidad * item.price
        cantidad = cantidad + subtotal
      })
      
      return  cantidad
      }
      
    }
  }
    
  
  
  
 

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
