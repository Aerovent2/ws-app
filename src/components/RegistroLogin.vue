<template>
  <div v-if="registro" class="container">
    <h1>Registrese</h1>
    <form>
      <div class="mb-3">
        <label for="nombre" class="form-label">Nombre</label>
        <input type="text" class="form-control" id="nombre" required v-model="usuario.nombre">
      </div>
            <div class="mb-3">
        <label for="apellido" class="form-label">Apellido</label>
        <input type="text" class="form-control" id="apellido" required v-model="usuario.apellido" >
      </div>
            <div class="mb-3">
        <label for="correo" class="form-label">Direccion de Correo</label>
        <input type="email" class="form-control" id="correo" required v-model="usuario.correo" >
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">Contraseña</label>
        <input type="password" class="form-control" id="password" required v-model="usuario.password">
      </div>
      <button type="button" class="btn btn-primary" @click="registrarme">Registrarme</button>
      <button type="button" class="btn btn-secondary" @click="esRegistro">Ya está Registrado?</button>
    </form>
  </div>

  <div v-else class="container p-5">
    <h1>Ingrese</h1>
    <form>
      <div class="mb-3">
        <label for="correo" class="form-label">Direccion de Correo</label>
        <input type="email" class="form-control" id="correo" required v-model="usuario.correo" >
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">Contraseña</label>
        <input type="password" class="form-control" id="password" required v-model="usuario.password">
      </div>
      <button type="button" class="btn btn-primary" @click="ingresar">Ingresar</button>
      <button type="button" class="btn btn-secondary" @click="esRegistro">No está Registrado?</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'RegistroLogin',
  props: {
   
  },
  data(){
    return{
      registro : false,
      usuario:{
        correo: "",
        nombre:"",
        apellido:"",
        password:""
      }
      
    }
  },
  methods:{
    esRegistro(){
      this.registro = !this.registro
    },
    registrarme(){
      if(this.usuario.apellido !== "" && this.usuario.correo !== "" && this.usuario.nombre !== "" && this.usuario.password !== ""){
        this.$emit('emitRegistro', this.usuario)
      }else{
        alert('complete todos los campos')
      }
      
    },
    ingresar(){
      if(this.usuario.correo !== "" && this.usuario.password !== ""){
        this.$emit('emitIngreso', this.usuario)
      }else{
        alert('complete todos los campos')
      }
      
    }
   
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
