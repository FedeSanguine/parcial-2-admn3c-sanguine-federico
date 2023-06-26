<template>
    <div>
        <imagen-grande :selectedImage="selectedImage"></imagen-grande>
        <div class="row">
            <div v-for="image in images" :key="image.id" class="col-md-3 col-sm-4 col-6"><a href="#" @click="showImage(image)"><img class="img-fluid" v-bind:src="image.thumbnail" /></a></div>

        </div>
    </div>
</template>
<script>
import ImagenGrande from './ImagenGrande.vue'
export default {
    props: ['images'],
    components: {ImagenGrande},
    data() {
        return{
            selectedImage: '',
        }
    },
    methods:{
        showImage: function (image){
            this.selectedImage = image
        }
    }
}
</script>
<style scoped>
img {
    max-width: 300px;
    max-height: 300px;


}

img:hover{
    filter: gray;
    -webkit-filter: grayscale(1);
}
</style>