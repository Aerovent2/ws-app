<template>
  <div id="app">
    <NavBar v-if="logueado" @emitNav="carritoChanger($event)" :currentUser="registrado"></NavBar>
    <RegistroLogin v-show="!logueado" @emitRegistro="registro($event)" @emitIngreso="ingreso($event)"></RegistroLogin>
    <ListaProductos v-show="logueado" v-if="!mostrarCarrito" @emitProductos="seleccionado($event)" ></ListaProductos>
    <ProductosDetail v-if="itemSeleccionado && !mostrarCarrito" :producto="itemSeleccionado" @emitDetail="alCarrito($event)"></ProductosDetail>
    <CarritoCompras v-if="mostrarCarrito" :itemsParaelCarrito="itemsCarrito" @emitCarrito="carritoChanger($event)"> </CarritoCompras>
    
    
  </div>
</template>

<script>


import RegistroLogin from './components/RegistroLogin.vue'
import ListaProductos from './components/ListaProductos.vue'
import NavBar from './components/NavBar.vue'
import ProductosDetail from './components/ProductosDetail.vue'
import CarritoCompras from './components/CarritoCompras.vue'


export default {
  name: 'App',
  components: {
    NavBar,
    RegistroLogin,
    ListaProductos,
    ProductosDetail,
    CarritoCompras
  },
  data(){
    return {
      admin: false,
      logueado:false,
      registrado:'',
      listaUsuarios: [ 
        { nombre: "leonardo", apellido: "heffel", correo: "leo_heffel@outlook.com", password: "1234" },
        { nombre: "pepe", apellido: "gonzalez", correo: "pepegonzalez@outlook.com", password: "1234" }
      ],
      itemSeleccionado: null,
      itemsCarrito:[],
      mostrarCarrito: false
    }
  },
  methods:{
    registro(payload){
     const {nombre, apellido, correo, password} = payload
     const nuevoUsuario= {nombre, apellido, correo:correo.toLowerCase() ,password}
     this.listaUsuarios.push(nuevoUsuario)
     this.registrado = nuevoUsuario
     this.logueado = true
    },
    ingreso(payload){
      const {correo, password} = payload
      const registrado = this.listaUsuarios.find(usuario => usuario.correo  == correo.toLowerCase())
      if(registrado){
        console.log('usuario encontrado')
        if(registrado.password == password){
          console.log('credenciales correctas')
          this.logueado = true
          this.registrado = registrado
          if(registrado.correo === "leo_heffel@outlook.com"){
            this.admin = true
          }
        }else{
          console.log('password no coincide')
        }
      }else{
        console.log('usuario inexistente')
      }
    },
    seleccionado(item){
      this.itemSeleccionado = item
    },
    alCarrito(payload){
      let {id, title, price, stock} = payload
      let enviar= {title,price,stock,id, cantidad:0}
      this.itemsCarrito.push(enviar)
    },
    carritoChanger(payload){
      this.mostrarCarrito = payload
    }
    
    
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
