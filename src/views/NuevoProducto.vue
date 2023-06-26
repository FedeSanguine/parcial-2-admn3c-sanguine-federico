<template>
    <v-container>
      <v-row class="text-center">

  
        <v-col class="mb-4">
          <h1 class="display-2 font-weight-bold mb-3">
            Agregar producto
          </h1>
          
          <v-form>
            <v-text-field
              solo
              name="input-1"
              label="Titulo"
              v-model="titulo"
            ></v-text-field>
            <v-text-field
              solo
              name="input-2"
              label="Descripcion"
              v-model="descripcion"
            ></v-text-field>
            <v-text-field
              solo
              type="number"
              name="input-3"
              label="Precio"
              v-model="precio"
            ></v-text-field>
            <v-select
            v-model="valor"
            :items="categorias"
            label="Categoria"
        ></v-select>
            <v-btn v-on:click="agregarProducto" color="primary" >Agregar</v-btn>
          </v-form>
        </v-col>
      </v-row>
    </v-container>

</template>

<script>
    export default {
        name: 'Nueva',
        props:['productos'],
        data(){
            return{
            index:0,
            titulo:'',
            descripcion:'',
            precio:'',
            categorias:['teclados','placas de video','monitores','mouses'],
            valor:[]
        }
        },
        methods: {
          agregarProducto: function(){
            var cont = this.productos.length;
            const producto = {
                titulo: this.titulo,
                descripcion: this.descripcion,
                precio: this.precio,
                categoria: this.valor,
                id: cont++,
                cant: 1
            }

            this.$emit('nuevoProducto', producto);
            this.$router.push('/productos');
          }
        }
    }

</script>