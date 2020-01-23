<template>
    <div class="hero-head">
        <header class="navbar">
            <div class="container">
                <div class="navbar-brand">
                    <b-navbar-item tag="router-link" :to="{ path: '/' }">
                        <!-- <img src="https://bulma.io/images/bulma-type-white.png" alt="Logo"> -->
                        <img id="logo" src="../assets/iclogo2.svg" alt="Logo">
                    </b-navbar-item>
                    <span class="navbar-burger burger" data-target="navbarMenuHeroC">
                        <span></span>
                        <span></span>
                        <span></span>
                    </span>
                </div>
                <div id="navbarMenuHeroC" class="navbar-menu">
                    <div class="navbar-end">
                        <router-link to="/" class="navbar-item has-text-weight-bold">
                            Inicio
                        </router-link>
                        <router-link to="/form" class="navbar-item has-text-weight-bold">
                            Registro Alumnos
                        </router-link>
                        <router-link to="/test" class="navbar-item has-text-weight-bold">
                            Test
                        </router-link>
                        <router-link to="/admin" class="navbar-item has-text-weight-bold">
                            <a class="button is-white">Administradores</a>
                        </router-link>
                    </div>
                </div>
            </div>
        </header>
    </div>
</template>

<script>
    export default {
        name: 'Navbar',
        data() {
            return {

            }
        }
    }

    document.addEventListener('DOMContentLoaded', () => {

        // Get all "navbar-burger" elements
        const $navbarBurgers = Array.prototype.slice.call(document.querySelectorAll('.navbar-burger'), 0);

        // Check if there are any navbar burgers
        if ($navbarBurgers.length > 0) {

            // Add a click event on each of them
            $navbarBurgers.forEach(el => {
                el.addEventListener('click', () => {

                    // Get the target from the "data-target" attribute
                    const target = el.dataset.target;
                    const $target = document.getElementById(target);

                    // Toggle the "is-active" class on both the "navbar-burger" and the "navbar-menu"
                    el.classList.toggle('is-active');
                    $target.classList.toggle('is-active');

                });
            });
        }

    });
</script>

<style>
    #logo {
        max-width: 100%;
        height: auto;
    }
</style>