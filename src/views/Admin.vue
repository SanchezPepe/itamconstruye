<template>
    <section>
        <section class="hero is-info is-bold">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">
                        Administración de alumnos
                    </h1>
                    <h2 class="subtitle">
                        Consulta, alta, baja y modificación de alumnos
                    </h2>
                </div>
            </div>
        </section>
        <!-- Botones para confirmar o cancelar -->
        <section class="block">
            <h1 class="subtitle">Acciones</h1>
            <div class="buttons container is-centered are-medium">
                <b-button class="has-text-weight-bold" type="is-info">
                    <router-link to="/" class="has-text-white">Alumnos</router-link>
                </b-button>
                <b-button class="has-text-weight-bold" type="is-info">
                    <router-link to="/" class="has-text-white">Configuración perfil</router-link>
                </b-button>
                <b-button class="has-text-weight-bold" type="is-danger">
                    <router-link to="/" class="has-text-white">Cerrar Sesión</router-link>
                </b-button>
            </div>
        </section>
    </section>

</template>

<script>
    export default {

    }
</script>

<style>
.block{
    padding: 3%;
}

</style>