<template>
  <div class="hero is-primary is-bold is-fullheight" id="app">
    <Navbar />

    <router-view />

    <Footer />
  </div>
</template>

<script>
  import Navbar from './components/Navbar'
  import Footer from './components/Footer'
  import 'buefy/dist/buefy.css'

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

<style lang="scss">
  // Import Bulma's core
  @import "~bulma/sass/utilities/_all";

  // Set your colors
  $primary: #035f1f;
  $primary-invert: findColorInvert($primary);
  $twitter: #4099FF;
  $twitter-invert: findColorInvert($twitter);

  // Setup $colors to use as bulma classes (e.g. 'is-twitter')
  $colors: ("white": ($white, $black),
    "black": ($black, $white),
    "light": ($light, $light-invert),
    "dark": ($dark, $dark-invert),
    "primary": ($primary, $primary-invert),
    "info": ($info, $info-invert),
    "success": ($success, $success-invert),
    "warning": ($warning, $warning-invert),
    "danger": ($danger, $danger-invert),
    "twitter": ($twitter, $twitter-invert));

  // Links
  $link: $primary;
  $link-invert: $primary-invert;
  $link-focus-border: $primary;

  $navbar-item-hover-background-color:hsla(0, 0%, 22%, 0.561);

  // Import Bulma and Buefy styles
  @import "~bulma";
  @import "~buefy/src/scss/buefy";
</style>