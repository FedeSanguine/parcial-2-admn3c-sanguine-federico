<template>
<v-container>
      <v-row class="text-center">
        <v-col class="mb-4">
          <h1 class="display-2 font-weight-bold mb-3">
            Productos
          </h1>
          <v-text-field
              solo
              name="input-busqueda"
              label="Buscar"
              v-model="busqueda"
            ></v-text-field>
            <v-menu
        bottom
        offset-y
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            class="ma-2"
            v-bind="attrs"
            v-on="on"
          >
            Filtrar por categoria
          </v-btn>
        </template>
        <v-list> 
            <v-checkbox v-model="checkTeclados" class="mr-2" label="Teclados" v-on:click="catTeclados"></v-checkbox>
            <v-checkbox v-model="checkPlacas" class="mr-2" label="Placas de video" v-on:click="catPlacas"></v-checkbox>
            <v-checkbox v-model="checkMonitores" class="mr-2" label="Monitores" v-on:click="catMonitores"></v-checkbox>
            <v-checkbox v-model="checkMouses" class="mr-2" label="Mouses" v-on:click="catMouses"></v-checkbox>
        </v-list>
      </v-menu>
          <v-menu
        bottom
        offset-y
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            class="ma-2"
            v-bind="attrs"
            v-on="on"
          >
          <v-badge inline :content="carritoL" ></v-badge>
            Carrito
            <v-badge inline v-text="`$`+carritoP" ></v-badge>
          </v-btn>
        </template>
        <v-list>
          <v-list-item
            v-for="(item, i) in carritoA"
            :key="i"
            @click="() => {}"
          > 
            <v-badge inline :content="item.cant" class="mr-2" ></v-badge>
            <v-list-item-title class="mr-2">{{ item.titulo }}</v-list-item-title>
            <v-badge inline v-text="`$`+ item.precio * item.cant" ></v-badge>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-menu
        bottom
        offset-y
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            class="ma-2"
            v-bind="attrs"
            v-on="on"
          >
            Filtrar por precio
          </v-btn>
        </template>
        <v-list>
            <v-checkbox v-model="checkMenor" class="mr-2" label="Menor precio" v-on:click="menorP"></v-checkbox>
            <v-checkbox v-model="checkMayor" class="mr-2" label="Mayor precio" v-on:click="mayorP"></v-checkbox>
        </v-list>
      </v-menu>
          <v-card
    class="mx-auto mt-4"
    max-width="600"
    outlined
    v-for="(producto, index) in productosFiltrados" v-bind:key="index"
  >
    <v-list-item three-line >
      <v-list-item-content>
        
        <v-list-item-title class="text-h5 mb-1" v-text="producto.titulo">
        </v-list-item-title>
        <v-badge
        inline
        :content="producto.categoria"
        ></v-badge>
        <v-img :src="producto.imagen" :alt="producto.imagen_descripcion"></v-img>
        <v-list-item-subtitle v-text="producto.descripcion"></v-list-item-subtitle>
        <p
        inline
        >${{producto.precio}}</p>
      <v-card-actions class="justify-center">
      <v-btn
        outlined
        rounded
        v-bind:to="'editar/'+producto.id"
      >
        Editar
      </v-btn>
      <v-btn v-on:click="agregarCarrito(producto)" color="primary" >Agregar al carrito</v-btn>
    </v-card-actions>
      </v-list-item-content>

      
    </v-list-item>
  </v-card>

        </v-col>
  
      </v-row>
    </v-container>
  </template>

  <script>
    export default {
      name: 'Productos',
      props:['productos'],
      data: () => ({
        carritoA: [],
        busqueda: '',
        checkTeclados: false,
        checkPlacas: false,
        checkMonitores: false,  
        checkMouses: false,
        checkMenor: false,
        checkMayor: false,
      }),
      computed:{
        productosFiltrados(){
            var array = this.productos;
            console.log(array)
            return array.filter(prod => prod.titulo.toLowerCase().includes(this.busqueda.toLowerCase()));
        },
        carritoL(){
          var acum = 0; 
          for(var i of this.carritoA){
            acum += i.cant;
          }
          return acum;
        },
        carritoP(){
          var acum2 = 0;
          for(var precios of this.carritoA){
            acum2 += precios.precio * precios.cant
          }
          return acum2;
        }
      },
      methods:{

        agregarCarrito(producto){
          var prodExistente;
          var existente = this.carritoA.filter((item, index)=>{
            if(item.id == Number(producto.id)){
              prodExistente = index;
              return true;
            }else{
              return false;
            }
          });

          if(existente.length){
                    this.carritoA[prodExistente].cant++
                    this.carritoA[prodExistente].precio = producto['precio']
                    this.carritoA[prodExistente].titulo = producto['titulo']
                }else{
                    this.carritoA.push({titulo: producto.titulo, precio: producto['precio'], cant: producto['cant'], id: producto['id']})
                    console.log(this.carritoA)
                }
        },

        catTeclados(){
          const cat= {
            categorias: 'teclados',
            check: this.checkTeclados
          } 
          this.$emit('catTeclados', cat, this.checkTeclados);
        },
        catPlacas(){
          const cat= {
            categorias: 'placas de video',
            check: this.checkPlacas
          } 
          this.$emit('catPlacas', cat, this.checkPlacas);
        },
        catMonitores(){
          const cat= {
            categorias: 'monitores',
            check: this.checkMonitores
          } 
          this.$emit('catTeclados', cat, this.checkMonitores);
        },
        catMouses(){
          const cat= {
            categorias: 'mouses',
            check: this.checkMouses
          } 
          this.$emit('catTeclados', cat, this.checkMouses);
        },
        menorP(){
          const checkMen={
            check: this.checkMenor,
          }
          this.$emit('menorP', checkMen, this.checkMenor)
        },
        mayorP(){
          const checkMay={
            check: this.checkMayor
          }
          this.$emit('mayorP', checkMay, this.checkMayor)
        }
      }

    }
  </script>