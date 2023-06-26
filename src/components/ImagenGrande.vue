<template>
    <div class="row">
        <div class="col-sm-5 col-12 imagen">
            <img :src="selectedImage.imageLink" class="img-fluid">
        </div>
        <div>
            <div class="col-sm-7 col-12 mt-4">
            <h2>{{selectedImage.title}}</h2>
            <p>{{selectedImage.description}}</p>
        </div>
        </div>

    </div>
</template>
<script>
    export default {
        props: ['selectedImage']
    }
</script>

<style>
h2{
    margin: 15px;
    padding-right: 30px ;
};

.imagen.img{
   max-width: 300px;
}
</style>