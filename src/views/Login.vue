<template>
    <section class="container is-vcentered">
        <link rel="stylesheet" href="https://cdn.materialdesignicons.com/2.5.94/css/materialdesignicons.min.css">
        <div class="box">
            <h2 class="subtitle has-text-black">Iniciar sesión</h2>
            
            <b-field label="Correo Electrónico">
                <b-input type="email" v-model="email" validation-message="Introduce un correo válido">
                </b-input>
            </b-field>
            <b-field label="Contraseña" expanded>
                <b-input type="password" value="" password-reveal>
                </b-input>
            </b-field>
            <br>
            <div class="buttons is-centered">
                <b-button tag="router-link" to="/admin" type="is-primary">
                    Iniciar sesión
                </b-button>
                <b-button tag="router-link" to="/" type="is-danger">
                    Cancelar
                </b-button>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'home',
        data() {
            return {
                validEmail: false
            }
        }

    }
</script>

<style>
.box{
    margin-top: 50%;
}

</style>