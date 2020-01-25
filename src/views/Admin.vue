<template>
    <section class="has-background-primary">
        <link rel="stylesheet" href="https://cdn.materialdesignicons.com/2.5.94/css/materialdesignicons.min.css">
        <section class="hero is-dark is-bold">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">
                        Registro de alumnos
                    </h1>
                </div>
            </div>
        </section>

        <section class="container">
            <div class="columns">
                <div class="column is-three-fifths box">
                    <p class="subtitle has-text-black">Acciones</p>
                    <div class="buttons">
                        <button class="button is-info is-medium">Administrar usuarios</button>
                        <button class="button is-info is-medium">Información alumnos</button>

                    </div>

                </div>
                <div class="column box">
                    <p class="subtitle has-text-black">Información del Usuario</p>
                    <button class="button is-medium is-info">Editar perfil</button>

                </div>
            </div>
            <section>
                <students></students>
            </section>

        </section>

    </section>
</template>

<script>
    import students from '../components/StudentTable'

    export default {
        name: 'AdminView',
        components: {
            students
        },
        methods: {}
    }
</script>

<style scoped>
    .subtitle {
        font-weight: bold;
    }

    .checkbox {
        padding-top: 10%;
    }

    .box {
        padding: 3.5%;
        margin: 1.5%;
    }
</style>