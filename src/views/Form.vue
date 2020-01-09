<template>
    <section>
        <link rel="stylesheet" href="https://cdn.materialdesignicons.com/2.5.94/css/materialdesignicons.min.css">
        <section class="hero is-medium is-primary is-bold">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">
                        Registro de alumnos
                    </h1>
                    <h2 class="subtitle">
                        ITAM Construye
                    </h2>
                </div>
            </div>
        </section>
        <br>
        <h2 class="subtitle">Información previa</h2>
        <section class="container info">
            <div class="block">
                <b-field label="¿El alumno ha estado inscrito en alguno de nuestros programas?" />
                <b-radio v-model="radio" name="name" native-value="Sí">
                    Sí
                </b-radio>
                <b-radio v-model="radio" name="name" native-value="No">
                    No
                </b-radio>
            </div>
        </section>

        <br>
        <h2 class="subtitle">Información del alumno</h2>
        <section class="container info has-text-centered">

            <!-- INFORMACION BASICA DEL ALUMNO -->
            <b-field grouped group-multiline>
                <b-field label="Nombre(s)" expanded>
                    <b-input type="text" v-model="studentName"></b-input>
                </b-field>
                <b-field label="Apellido Paterno" expanded>
                    <b-input type="text" v-model="studentFLN"></b-input>
                </b-field>
                <b-field label="Apellido Materno" expanded>
                    <b-input type="text" v-model="studentMLN"></b-input>
                </b-field>
            </b-field>
            <b-field grouped group-multiline>
                <b-field label="Fecha de nacimiento" expanded>
                    <b-datepicker :show-week-number="showWeekNumber" :month-names="monthEs" :dayNames="daysEs"
                        :years-range="yearsRange" placeholder="Seleccionar fecha" icon="calendar-today"
                        :format="DatePickerFormat">
                    </b-datepicker>
                </b-field>
            </b-field>
            <br>
            <b-field label="Condiones médicas y/o alergias">
                <b-input maxlength="200" type="textarea"></b-input>
            </b-field>

            <!-- INFORMACIÓN ESCOLAR DEL ALUMNO -->
            <b-field grouped group-multiline>
                <b-field label="Grado Escolar" expanded>
                    <b-input type="text" v-model="studentName"></b-input>
                </b-field>
                <b-field label="Sabe leer?" expanded>
                    <div class="block">
                        <b-radio v-model="radio" name="name" native-value="Sí">
                            Sí
                        </b-radio>
                        <b-radio v-model="radio" name="name" native-value="No">
                            No
                        </b-radio>
                    </div>
                </b-field>
            </b-field>
        </section>

        <br>
        <h2 class="subtitle">Información de padre, madre o tutor</h2>
        <section class="container info">
            <b-field grouped group-multiline>
                <b-field label="Nombre(s)" expanded>
                    <b-input type="text" v-model="tutorName"></b-input>
                </b-field>
                <b-field label="Apellido Paterno" expanded>
                    <b-input type="text" v-model="tutorFLN"></b-input>
                </b-field>
                <b-field label="Apellido Materno" expanded>
                    <b-input type="text" v-model="tutorMLN"></b-input>
                </b-field>
            </b-field>

            <b-field grouped group-multiline>
                <b-field label="Teléfono" expanded>
                    <b-input type="text" v-model="phone"></b-input>
                </b-field>
                <b-field label="Correo Electrónico" expanded>
                    <b-input type="text" v-model="email"></b-input>
                </b-field>
                <b-field label="Volver a escribir correo" expanded>
                    <b-input type="text" v-model="validateEmail"></b-input>
                </b-field>
            </b-field>
        </section>
        <br>
        <div class="buttons container is-centered">
            <b-button type="is-success" size="is-medium">Registrar</b-button>
            <b-button type="is-danger" size="is-medium">Cancelar</b-button>
        </div>
        <br>
    </section>
</template>

<script>
    export default {
        name: 'Footer',
        data() {
            return {
                monthEs: ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre',
                    'Octubre', 'Noviembre', 'Diciembre'
                ],
                daysEs: ['Do', 'Lu', 'Ma', 'Mi', 'Ju', 'Vi', 'Sa'],
                yearsRange: [-30, 0]

            }
        }
    }
</script>

<style scoped>
    .info {
        border: solid black 1px;
        padding: 15px;
    }
</style>