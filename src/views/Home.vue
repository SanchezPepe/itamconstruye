<template>
  <div class="home">
    <h1 class="title has-text-white">Sistema de Información ITAM Construye</h1>
    <img alt="Vue logo" src="http://www.itamconstruye.itam.mx/wp-content/uploads/cropped-Logo_sinfondoBLANCO.png">
    <h2 class="has-text-white"> Acerca de ITAM Construye </h2>
    <p>
      ITAM Construye es una organización formada por estudiantes del Instituto Tecnológico Autónomo de México que buscan
      incidir en la sociedad a través de acciones que solucionen los problemas que nos rodean, actuando más allá de las
      aulas.
    </p>
    <HelloWorld msg="Welcome to Your Vue.js Add" />
  </div>
</template>

<script>
  // @ is an alias to /src
  import HelloWorld from '@/components/Hello.vue'

  export default {
    name: 'home',
    components: {
      HelloWorld
    }
  }
</script>

<style>
  .home {
    background-color: black;
  }
</style>