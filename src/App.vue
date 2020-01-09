<template>
  <div id="app">
    <Navbar />

    <router-view />

    <Footer/>
  </div>
</template>

<script>
  import Navbar from './components/Navbar'
  import Footer from './components/Footer'

  export default {
    name: 'app',
    components: {
      Navbar,
      Footer
    }
  }
</script>

<style>
  html,
  body {
    height: 100%;
    margin: 0%;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    height: 100%;
  }
</style>