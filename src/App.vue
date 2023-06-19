<template>
  <v-app>
    <v-app-bar
      app
      color="black"
      dark
    >
      <div class="d-flex align-center">
        <router-link to="/">

        <v-img
          alt="Keyware"
          class=" mt-1 hidden-sm-and-down"
          contain
          min-width="50"
          :src="require('./assets/logo-2.png')"
          width="50"
        />
        </router-link>
      </div>

      <v-spacer></v-spacer>

      
      <v-btn text
        to="/">
        <span class="mr-2">Home</span>
        <v-icon>mdi-home</v-icon>
      </v-btn>

      <v-btn text
        to="/productos">
        <span class="mr-2">Productos</span>
        <v-icon>mdi-eye</v-icon>
      </v-btn>

      <v-btn text
        to="/nuevoproducto">
        <span class="mr-2">Nuevo producto</span>
        <v-icon>mdi-pencil</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view
        v-bind:productos="productos"
        v-on:nuevoProducto="agregarProducto"
        v-on:guardarProducto="guardarProducto"
        v-on:borrarProducto="borrarProducto"
        v-on:catTeclados="catTeclados"
        v-on:catPlacas="catPlacas"
        v-on:catMonitores="catMonitores"
        v-on:catMouses="catMouses"
        v-on:menorP="menorP"
        v-on:mayorP="mayorP"
      />
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  created: function(){
      this.guardarProductoLocal();
  },
  data: () => ({
    productos: 
      [{
        titulo: "Hyper x Alloy Origins 65",
        descripcion: "Teclado mecánico con switches hyper x red de tacto lineal, cuerpo de aluminio aeroespacial",
        precio: 10000,
        imagen: "https://cdn.shopify.com/s/files/1/0564/3612/9997/products/hyperx_alloy_origins_65_english_us_1_top_down_e5b90472-608b-44b3-b451-825c2ebde986_2048x2048.jpg?v=1665613630",
        imagen_descripcion: "Hyper x Alloy Origins 65",
        categoria: 'teclados',
        cant: 1,
        id: 0
      },
      {
        titulo: "GeForce RTX 3060 12GB",
        descripcion: "Placa de video Nvidia serie 3060 - Tamaño y tipo de memoria: 12Gb GDDR6  - Consumo de energía: 170W",
        precio: 30000,
        imagen: "https://www.venex.com.ar/products_images/1622652569_df564g1h.png",
        imagen_descripcion: "GeForce RTX 3060 12GB",
        categoria: 'placas de video',
        cant: 1,
        id: 1
      },
      {
        titulo: "Acer 144hz 24",
        descripcion: "Monitor gamer de la marca Acer - Tasa de refresco: 144Hz - Resolución de pantalla: 1920 x 1080",
        precio: 50000,
        imagen: "https://arrichetta.com.ar/wp-content/uploads/2020/05/UM.FX1AA.P02-1.jpg",
        imagen_descripcion: "Acer 144hz 24",
        categoria: 'monitores',
        cant: 1,
        id: 2
      },
      {
        titulo: "Logitech g502 mouse gamer",
        descripcion: "G502 Hero dispone de un sensor óptico avanzado para máxima precisión de seguimiento, iluminación RGB personalizada, perfiles de juego personalizados, de 200 a 16.000 dpi y pesas reposicionables.",
        precio: 20000,
        imagen: "https://s3-sa-east-1.amazonaws.com/saasargentina/twIa9uceTfTpbH4ZDwdX/imagen",
        imagen_descripcion: "Logitech g502 mouse gamer",
        categoria: 'mouses',
        cant: 1,
        id: 3
      },
      {
        titulo: "Razer Huntsman Tournament",
        descripcion: "El Razer Huntsman Tournament  es un teclado no numérico con cable desmontable - puerto USB-C - iluminación RGB - teclas de PBT",
        precio: 30000,
        imagen: "https://www.fullh4rd.com.ar/img/productos/Pics_Prod/teclado-gamer-razer-huntsman-tournament-edition-87-teclas-0.jpg",
        imagen_descripcion: "Razer Huntsman Tournament",
        categoria: 'teclados',
        cant: 1,
        id: 4
      },
      {
        titulo: "Redragon Kumara k552",
        descripcion: "El Kumara es un teclado mecánico TKL (sin pad numérico) compacto, pero ampliamente funcional.",
        precio: 50000,
        imagen: "https://www.brandimia.com/productos/K552-2-SP-3.jpg",
        imagen_descripcion: "Redragon Kumara k552",
        categoria: 'teclados',
        cant: 1,
        id: 5
      },
      {
        titulo: "Hyper x Alloy fps pro",
        descripcion: "Teclado mecánico para videojuegos HyperX Alloy FPS Pro El HyperX™ Alloy FPS Pro es para el jugador FPS que desea un teclado sin tenkey (TKL) fiable y preciso que le permita aumentar su espacio del escritorio.",
        precio: 20000,
        imagen: "https://spacegamer.com.ar/img/Public/1058-producto-1019-producto-teclado-hyperx-alloy-fps-pro-blue-mecanico-3-2424-101.jpg",
        imagen_descripcion: "Hyper x Alloy fps pro",
        categoria: 'teclados',
        cant: 1,
        id: 6
      },

      ],
      prod2:[{
        titulo: "Hyper x Alloy Origins 65",
        descripcion: "Teclado mecánico con switches hyper x red de tacto lineal, cuerpo de aluminio aeroespacial",
        precio: 10000,
        imagen: "https://cdn.shopify.com/s/files/1/0564/3612/9997/products/hyperx_alloy_origins_65_english_us_1_top_down_e5b90472-608b-44b3-b451-825c2ebde986_2048x2048.jpg?v=1665613630",
        imagen_descripcion: "Hyper x Alloy Origins 65",
        categoria: 'teclados',
        cant: 1,
        id: 0
      },
      {
        titulo: "GeForce RTX 3060 12GB",
        descripcion: "Placa de video Nvidia serie 3060 - Tamaño y tipo de memoria: 12Gb GDDR6  - Consumo de energía: 170W",
        precio: 30000,
        imagen: "https://www.venex.com.ar/products_images/1622652569_df564g1h.png",
        imagen_descripcion: "GeForce RTX 3060 12GB",
        categoria: 'placas de video',
        cant: 1,
        id: 1
      },
      {
        titulo: "Acer 144hz 24",
        descripcion: "Monitor gamer de la marca Acer - Tasa de refresco: 144Hz - Resolución de pantalla: 1920 x 1080",
        precio: 50000,
        imagen: "https://arrichetta.com.ar/wp-content/uploads/2020/05/UM.FX1AA.P02-1.jpg",
        imagen_descripcion: "Acer 144hz 24",
        categoria: 'monitores',
        cant: 1,
        id: 2
      },
      {
        titulo: "Logitech g502 mouse gamer",
        descripcion: "G502 Hero dispone de un sensor óptico avanzado para máxima precisión de seguimiento, iluminación RGB personalizada, perfiles de juego personalizados, de 200 a 16.000 dpi y pesas reposicionables.",
        precio: 20000,
        imagen: "https://s3-sa-east-1.amazonaws.com/saasargentina/twIa9uceTfTpbH4ZDwdX/imagen",
        imagen_descripcion: "Logitech g502 mouse gamer",
        categoria: 'mouses',
        cant: 1,
        id: 3
      },
      {
        titulo: "Razer Huntsman Tournament",
        descripcion: "El Razer Huntsman Tournament  es un teclado no numérico con cable desmontable - puerto USB-C - iluminación RGB - teclas de PBT",
        precio: 30000,
        imagen: "https://www.fullh4rd.com.ar/img/productos/Pics_Prod/teclado-gamer-razer-huntsman-tournament-edition-87-teclas-0.jpg",
        imagen_descripcion: "Razer Huntsman Tournament",
        categoria: 'teclados',
        cant: 1,
        id: 4
      },
      {
        titulo: "Redragon Kumara k552",
        descripcion: "El Kumara es un teclado mecánico TKL (sin pad numérico) compacto, pero ampliamente funcional.",
        precio: 50000,
        imagen: "https://www.brandimia.com/productos/K552-2-SP-3.jpg",
        imagen_descripcion: "Redragon Kumara k552",
        categoria: 'teclados',
        cant: 1,
        id: 5
      },
      {
        titulo: "Hyper x Alloy fps pro",
        descripcion: "Teclado mecánico para videojuegos HyperX Alloy FPS Pro El HyperX™ Alloy FPS Pro es para el jugador FPS que desea un teclado sin tenkey (TKL) fiable y preciso que le permita aumentar su espacio del escritorio.",
        precio: 20000,
        imagen: "https://spacegamer.com.ar/img/Public/1058-producto-1019-producto-teclado-hyperx-alloy-fps-pro-blue-mecanico-3-2424-101.jpg",
        imagen_descripcion: "Hyper x Alloy fps pro",
        categoria: 'teclados',
        cant: 1,
        id: 6
      },

      ]
  }),
  methods:{
    agregarProducto: function(producto){
      this.productos.push(producto);
      localStorage.setItem('productos', JSON.stringify(this.productos));
    },
    traerProductos: function(){
      const productos = JSON.parse(localStorage.getItem('productos'));
      this.productos = productos ? productos : [];
    },
    guardarProducto: function(producto){
      this.productos[producto.index].titulo = producto.titulo;
      this.productos[producto.index].descripcion = producto.descripcion;
      this.productos[producto.index].precio = producto.precio;
      this.productos[producto.index].categoria = producto.categoria;
      localStorage.setItem('productos', JSON.stringify(this.productos));
    },
    borrarProducto: function(index){
      this.productos.splice(index, 1);
      localStorage.setItem('productos', JSON.stringify(this.productos));
    },
    guardarProductoLocal: function(productos){
      productos = 
        [{
        titulo: "Hyper x Alloy Origins 65",
        descripcion: "Teclado mecánico con switches hyper x red de tacto lineal, cuerpo de aluminio aeroespacial",
        precio: 10000,
        imagen: "https://cdn.shopify.com/s/files/1/0564/3612/9997/products/hyperx_alloy_origins_65_english_us_1_top_down_e5b90472-608b-44b3-b451-825c2ebde986_2048x2048.jpg?v=1665613630",
        imagen_descripcion: "Hyper x Alloy Origins 65",
        categoria: 'teclados',
        cant: 1,
        id: 0
        },
        {
        titulo: "GeForce RTX 3060 12GB",
        descripcion: "Placa de video Nvidia serie 3060 - Tamaño y tipo de memoria: 12Gb GDDR6  - Consumo de energía: 170W",
        precio: 30000,
        imagen: "https://www.venex.com.ar/products_images/1622652569_df564g1h.png",
        imagen_descripcion: "GeForce RTX 3060 12GB",
        categoria: 'placas de video',
        cant: 1,
        id: 1
        },
        {
        titulo: "Acer 144hz 24",
        descripcion: "Monitor gamer de la marca Acer - Tasa de refresco: 144Hz - Resolución de pantalla: 1920 x 1080",
        precio: 50000,
        imagen: "https://arrichetta.com.ar/wp-content/uploads/2020/05/UM.FX1AA.P02-1.jpg",
        imagen_descripcion: "Acer 144hz 24",
        categoria: 'monitores',
        cant: 1,
        id: 2
        },
        {
        titulo: "Logitech g502 mouse gamer",
        descripcion: "G502 Hero dispone de un sensor óptico avanzado para máxima precisión de seguimiento, iluminación RGB personalizada, perfiles de juego personalizados, de 200 a 16.000 dpi y pesas reposicionables.",
        precio: 20000,
        imagen: "https://s3-sa-east-1.amazonaws.com/saasargentina/twIa9uceTfTpbH4ZDwdX/imagen",
        imagen_descripcion: "Logitech g502 mouse gamer",
        categoria: 'mouses',
        cant: 1,
        id: 3
        },
        {
        titulo: "Razer Huntsman Tournament",
        descripcion: "El Razer Huntsman Tournament  es un teclado no numérico con cable desmontable - puerto USB-C - iluminación RGB - teclas de PBT",
        precio: 30000,
        imagen: "https://www.fullh4rd.com.ar/img/productos/Pics_Prod/teclado-gamer-razer-huntsman-tournament-edition-87-teclas-0.jpg",
        imagen_descripcion: "Razer Huntsman Tournament",
        categoria: 'teclados',
        cant: 1,
        id: 4
        },
        {
        titulo: "Redragon Kumara k552",
        descripcion: "El Kumara es un teclado mecánico TKL (sin pad numérico) compacto, pero ampliamente funcional.",
        precio: 50000,
        imagen: "https://www.brandimia.com/productos/K552-2-SP-3.jpg",
        imagen_descripcion: "Redragon Kumara k552",
        categoria: 'teclados',
        cant: 1,
        id: 5
        },
        {
        titulo: "Hyper x Alloy fps pro",
        descripcion: "Teclado mecánico para videojuegos HyperX Alloy FPS Pro El HyperX™ Alloy FPS Pro es para el jugador FPS que desea un teclado sin tenkey (TKL) fiable y preciso que le permita aumentar su espacio del escritorio.",
        precio: 20000,
        imagen: "https://spacegamer.com.ar/img/Public/1058-producto-1019-producto-teclado-hyperx-alloy-fps-pro-blue-mecanico-3-2424-101.jpg",
        imagen_descripcion: "Hyper x Alloy fps pro",
        categoria: 'teclados',
        cant: 1,
        id: 6
        },
        ];
      localStorage.setItem('productos', JSON.stringify(productos));
    },
    catTeclados: function(cat, checkTeclados){
      if(checkTeclados){
        var array2 = this.productos.filter(item => item.categoria == cat.categorias)
      console.log(array2)
      this.productos = array2
      return this.productos
      }else{
        return this.productos = this.prod2
      }
      
    },
    catPlacas: function(cat, checkPlacas){
      if(checkPlacas){
        var array2 = this.productos.filter(item => item.categoria == cat.categorias)
      console.log(array2)
      this.productos = array2
      return this.productos
      }else{
        return this.productos = this.prod2
      }
    },
    catMonitores: function(cat, checkMonitores){
      if(checkMonitores){
        var array2 = this.productos.filter(item => item.categoria == cat.categorias)
      console.log(array2)
      this.productos = array2
      return this.productos
      }else{
        return this.productos = this.prod2
      }
    },
    catMouses: function(cat, checkMouses){
      if(checkMouses){
        var array2 = this.productos.filter(item => item.categoria == cat.categorias)
      console.log(array2)
      this.productos = array2
      return this.productos
      }else{
        return this.productos = this.prod2
      }
    },
    menorP: function(checkMen, checkMenor){
      if(checkMenor){
         var array2 = this.productos.sort((a,b) => (a.precio > b.precio) ? 1 : -1)
      console.log(array2)
      this.productos = array2
      return this.productos
      }else{
        return this.productos = this.prod2
      }
    },
    mayorP: function(checkMay, checkMayor){
      if(checkMayor){
         var array2 = this.productos.sort((a,b) => (a.precio < b.precio) ? 1 : -1)
      console.log(array2)
      this.productos = array2
      return this.productos
      }else{
        return this.productos = this.prod2
      }
    }
  }
};
</script>
