<template>
    <b-navbar>
        <template slot="brand">
            <b-navbar-item tag="router-link" :to="{ path: '/' }">
                <img src="https://raw.githubusercontent.com/buefy/buefy/dev/static/img/buefy-logo.png"
                    alt="Lightweight UI components for Vue.js based on Bulma">
            </b-navbar-item>
        </template>
        
        <template slot="start">
            <b-navbar-item href="#">
                <router-link to="/" class="navbar-item has-text-weight-bold">Home</router-link>
            </b-navbar-item>
            <b-navbar-item href="#">
                <router-link to="/about" class="navbar-item has-text-weight-bold">About</router-link>
            </b-navbar-item>
            <b-navbar-item href="#">
                <router-link to="/form" class="navbar-item has-text-weight-bold">Form</router-link>
            </b-navbar-item>
        </template>

        <template slot="end">
            <b-navbar-item tag="div">
                <a class="button is-primary">
                    <strong>Administradores</strong>
                </a>
            </b-navbar-item>
        </template>
    </b-navbar>
</template>

<script>
    export default {
        name: 'Navbar',
        data() {
            return {

            }
        }

    }
</script>