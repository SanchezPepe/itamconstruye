<template>
    <div class="hero-head">
        <header class="navbar">
            <div class="container">
                <div class="navbar-brand">
                    <b-navbar-item tag="router-link" :to="{ path: '/' }">
                        <img src="https://bulma.io/images/bulma-type-white.png" alt="Logo">
                    </b-navbar-item>
                    <a class="navbar-item">
                        <!-- <img src="../assets/iclogo.png" alt="Logo"> -->
                    </a>
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
                            <a class="button is-primary">Administradores</a>
                        </router-link>
                    </div>
                </div>
            </div>
        </header>
    </div>
    <!-- <b-navbar class="is-black">
        <template slot="brand">
            <b-navbar-item tag="router-link" :to="{ path: '/' }">
                <p>ITAM Construye - SI</p>
            </b-navbar-item>
        </template>

        <template slot="start">
            <b-navbar-item href="#">
                <router-link to="/form" class="navbar-item has-text-weight-bold">Registro Alumnos</router-link>
            </b-navbar-item>
            <b-navbar-item href="#">
                <router-link to="/test" class="navbar-item has-text-weight-bold">Test</router-link>
            </b-navbar-item>
        </template>

        <template slot="end">
            <b-navbar-item tag="div">
                <router-link to="/admin">
                    <a class="button is-primary">
                        <strong>Login Administradores</strong>
                    </a>
                </router-link>
            </b-navbar-item>
    
        </template>
        
    </b-navbar> -->

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