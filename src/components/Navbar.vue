<template>
    <b-navbar class="is-black">
        <template slot="brand">
            <b-navbar-item tag="router-link" :to="{ path: '/' }">
                <p>ITAM Construye - SI</p>
            </b-navbar-item>
        </template>
        
        <template slot="start">
            <b-navbar-item href="#">
                <router-link to="/" class="navbar-item has-text-weight-bold">Inicio</router-link>
            </b-navbar-item>
            <b-navbar-item href="#">
                <router-link to="/form" class="navbar-item has-text-weight-bold">Registro Alumnos</router-link>
            </b-navbar-item>
            <b-navbar-item href="#">
                <router-link to="/test" class="navbar-item has-text-weight-bold">Test</router-link>
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