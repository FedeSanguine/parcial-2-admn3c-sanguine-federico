
<template>
    <div class="galeria container mt-4">
        <lista-imagenes :images="images"></lista-imagenes>
    </div>
</template>

<script>
import ListaImagenes from './ListaImagenes.vue'
export default {
    name: 'Galeria',
  components: { ListaImagenes },
    data () {
        return{
            selectedImage: '',
            images: [
                {id: 1, title: 'Proximamente en Keyware', description: 'Mouse Noga X250R', thumbnail: 'https://http2.mlstatic.com/D_NQ_NP_698474-MLA28019302898_082018-O.webp', imageLink: 'https://http2.mlstatic.com/D_NQ_NP_698474-MLA28019302898_082018-O.webp' },
                {id: 2, title: 'Proximamente en Keyware', description: 'Monitor DELL XGaming', thumbnail: 'https://http2.mlstatic.com/D_NQ_NP_738555-MLA48984133517_012022-O.webp', imageLink: 'https://http2.mlstatic.com/D_NQ_NP_738555-MLA48984133517_012022-O.webp' },
                {id: 3, title: 'Proximamente en Keyware', description: 'Audiculares Redragon X150F', thumbnail: 'https://http2.mlstatic.com/D_NQ_NP_612294-MLA52221546173_102022-O.webp', imageLink: 'https://http2.mlstatic.com/D_NQ_NP_612294-MLA52221546173_102022-O.webp' },
                {id: 4, title: 'Proximamente en Keyware', description: 'Teclado GX Gaming', thumbnail: 'https://http2.mlstatic.com/D_NQ_NP_849852-MLA40161644321_122019-O.webp', imageLink: 'https://http2.mlstatic.com/D_NQ_NP_849852-MLA40161644321_122019-O.webp'  },
            ],
        }
    },
}

</script>

<style scoped>
img{
    -webkit-box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.2);
    -moz-box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.2);
    box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.2);
    margin-bottom: 20px;
}

img:hover{
    filter: gray;
    -webkit-filter: grayscale(1);
}
</style>
