<template>
    <v-container>
      <v-row class="text-center">

  
        <v-col class="mb-4">
          <h1 class="display-2 font-weight-bold mb-3">
            Editar producto
            <span hidden>{{ this.$route.params.id }}</span>
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
            <v-btn v-on:click="guardarProducto" color="primary" >Editar</v-btn>
            <v-btn class="ml-2" color="error" v-on:click="borrarProducto">Eliminar</v-btn>

          </v-form>

        </v-col>
  
      </v-row>
    </v-container>

</template>

<script>

export default{
    name: 'EditarArticulo',
    created(){
        this.index = this.$route.params.id;
        const data = JSON.parse (localStorage.getItem('productos'));
        const producto = data ? data[this.index] : {};

        this.titulo = producto.titulo ? producto.titulo : '';
        this.descripcion = producto.descripcion ? producto.descripcion : '';
        this.precio = producto.precio ? producto.precio : '';
        this.valor = producto.categoria ? producto.categoria : '';
    },
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
    methods:{
        guardarProducto: function(){
            const producto = {
                titulo: this.titulo,
                descripcion: this.descripcion,
                precio: this.precio,
                categoria: this.valor,
                index: this.index
            }

            this.$emit('guardarProducto', producto);
            this.$router.push('/productos');
        },
        borrarProducto: function(){
            this.$emit('borrarProducto', this.index);
            this.$router.push('/productos');
        }
    }
}

</script>