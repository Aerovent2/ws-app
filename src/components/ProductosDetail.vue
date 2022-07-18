<template>
<div class="container d-flex justify-content-center ">
  <div class="card" style="width: 18rem;">
    <img :src="producto.pictureUrl" class="card-img-top " style="max-height: 200px" alt="no se cargo la imagen">
    <div class="card-body">
      <h5 class="card-title">{{producto.title}}</h5>
      <p class="card-text">{{producto.description}}</p>
      <p class="card-text">${{producto.price}}</p>
      <p class="card-text">Unidades disponibles:  {{producto.stock}}</p>
      <a href="#" class="btn btn-primary" @click="agregarCarrito(producto)">Agregar al carrito</a>
    </div>
  </div>
</div>
  
</template>

<script>
export default {
  name: 'ProductosDetail',
  props:['producto'],
  methods:{
    agregarCarrito(payload){
      this.$emit('emitDetail', payload)
    }
  },
  
  }
 

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
