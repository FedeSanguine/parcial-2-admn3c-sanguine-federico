<template>
  <div class="home">
  <hello-world />
  <galeria />
</div>
</template>

<script>
  import HelloWorld from '../components/HelloWorld'
  import Galeria from '../components/Galeria'

  export default {
    name: 'Home',

    components: {
      HelloWorld,
      Galeria
    },
  }
</script>
