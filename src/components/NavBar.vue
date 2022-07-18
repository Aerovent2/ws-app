<template>
  <nav class="navbar navbar-expand-lg bg-light">
  <div class="container-fluid d-flex justify-content-between" >
    <a class="navbar-brand" href="#">Hola  {{currentUser.nombre}}</a>
    

      
        
  <button class="btn btn-outline-success" @click="verCarrito()" type="submit">Carrito</button>
     
  </div>
</nav>
</template>

<script>
export default {
  name: 'NavBar',
  props:['currentUser'],
  methods:{
    verCarrito(){
      this.$emit('emitNav', true)
    }
  },
  
  }
 

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
