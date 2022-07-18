<template>
  <div class="container ">
     <div class="row">
        <div v-for="item in productos" :key="item.id" class="card  " style="width: 18rem; ">
          
          <div class="card-body">
            <h5 class="card-title">{{item.title}}</h5>
            <a  class="btn btn-primary" @click="seleccionado(item)">Ver Detalles</a>
          </div>
        </div>

     </div>
  </div>
</template>



<script>


export default {
  name: 'ListaProductos',
  data(){
    return{
    productos: [
    {
        "id": 1,
        "title": "Mouse Logitech M280",
        "description": "Mouse inalambrico negro",
        "price": 1550,
        "pictureUrl": "https://http2.mlstatic.com/D_NQ_NP_697642-MLA32148169261_092019-O.webp",
        "category": "perifericos",
        "stock": 50
    },
    {
        "id": 2,
        "title": "Teclado Gadnic ZT900",
        "description": "Teclado gamer español Utemu",
        "price": 4499,
        "pictureUrl": "https://http2.mlstatic.com/D_NQ_NP_981064-MLA48646315070_122021-O.webp",
        "category": "perifericos",
        "stock": 21
    },
    {
        "id": 3,
        "title": "Parlante HP DS-2101",
        "description": "Parlante HP negro potencia 15w",
        "price": 3950,
        "pictureUrl": "https://http2.mlstatic.com/D_NQ_NP_923943-MLA45738471521_042021-O.webp",
        "category": "perifericos",
        "stock": 62
    },
    {
        "id": 4,
        "title": "Resma A4 75gr",
        "description": "Resma A4 Papel Autor 75 Gramos 500 Hojas",
        "price": 850,
        "pictureUrl": "https://http2.mlstatic.com/D_NQ_NP_821505-MLA45390777924_032021-O.webp",
        "category": "resmas",
        "stock": 33
    },
    {
        "id": 5,
        "title": "Resma A4 80gr",
        "description": "Resma Autor A4 Papel 80 Gramos 500 Hojas",
        "price": 1550,
        "pictureUrl": "https://http2.mlstatic.com/D_NQ_NP_644769-MLA47358485090_092021-O.webp",
        "category": "resmas","stock": 100
    },
    {
        "id": 6,
        "title": "Resma A4 90gr",
        "description": "Resma Report A4 Papel 90 Gramos 500 Hojas",
        "price": 1780,
        "pictureUrl": "https://http2.mlstatic.com/D_NQ_NP_923756-MLA47023891569_082021-O.webp",
        "category": "resmas",
        "stock": 40
    },
    {
        "id": 7,
        "title": "Cartucho HP 664n",
        "description": "Cartucho HP 664 Negro Original",
        "price": 2065,
        "pictureUrl": "https://http2.mlstatic.com/D_NQ_NP_802798-MLA44805275128_022021-O.webp",
        "category": "tintas",
        "stock": 15
    },
    {
        "id": 8,
        "title": "Cartucho HP 664c",
        "description": "Cartucho HP 664 Color Original",
        "price": 2390,
        "pictureUrl": "https://http2.mlstatic.com/D_NQ_NP_963228-MLA31009512160_062019-O.webp",
        "category": "tintas",
        "stock": 2
    }
                ]
        
    }
  },
  methods:{
    seleccionado(item){
      this.$emit('emitProductos', item)
    }
  }
 
}
</script>
