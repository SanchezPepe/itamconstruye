<template>
  <div class="home">
    <div class="hero-body has-text-centered">
      <div class="container">
        <h1 class="title">Sistema de Información ITAM Construye</h1>
        <img alt="IC logo" src="http://www.itamconstruye.itam.mx/wp-content/uploads/cropped-Logo_sinfondoBLANCO.png">
        <h2 class="subtitle">
          ITAM Construye es una organización formada por estudiantes del Instituto Tecnológico Autónomo de México que
          buscan
          incidir en la sociedad a través de acciones que solucionen los problemas que nos rodean, actuando más allá
          de las
          aulas.
        </h2>
        <br>
        <div class="logos">
            <a href="https://www.facebook.com/ITAMConstruye/" target="_blank">
              <figure hr class="image is-32x32">
                <img class="icons" src="https://bit.ly/2FvRUKz" alt="">
              </figure>
            </a>
            <a href="https://www.instagram.com/itamconstruye/" target="_blank">
              <figure class="image is-32x32">
                <img class="icons" src="https://bit.ly/2FzTewg" alt="">
              </figure>
            </a>
            <a href="https://twitter.com/ITAMConstruye" target="_blank">
              <figure class="image is-32x32">
                <img class="icons" src="https://bit.ly/37SsTWq" alt="">
              </figure>
            </a>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
  // @ is an alias to /src
  export default {
    name: 'home',
    components: {}
  }
</script>

<style>
.logos{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
</style>