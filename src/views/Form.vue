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
                <b-radio v-model="previous" name="name" native-value="true">
                    Sí
                </b-radio>
                <b-radio v-model="previous" name="name" native-value="false">
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
                    <b-input type="text" v-model="studentName" required
                        validation-message="El campo no puede estar vacío"></b-input>
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
                        :format="DatePickerFormat" v-model="birthDate">
                    </b-datepicker>
                </b-field>
                <b-field label="Condiciones médicas y/o alergias" expanded>
                    <b-input type="textarea" v-model="medicalInfo"></b-input>
                </b-field>
            </b-field>

            <!-- INFORMACIÓN ESCOLAR DEL ALUMNO -->
            <b-field grouped group-multiline>
                <b-field label="Grado Escolar" expanded>
                    <b-input type="text" v-model="grade"></b-input>
                </b-field>
                <b-field label="Sabe leer?" expanded>
                    <div class="block">
                        <b-radio v-model="reads" name="name" native-value="Sí">
                            Sí
                        </b-radio>
                        <b-radio v-model="reads" name="name" native-value="No">
                            No
                        </b-radio>
                    </div>
                </b-field>
            </b-field>
        </section>

        <!-- Información del tutor -->
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
                    <b-input type="email" v-model="phone" minlength="5"
                        validation-message="Introduce un teléfono valido"></b-input>
                </b-field>
                <b-field label="Correo Electrónico" expanded>
                    <b-input type="email" v-model="email" validation-message="Introduce un correo válido"></b-input>
                </b-field>
                <b-field :type="validationEmails" :message="valmsg" label="Volver a escribir correo" expanded>
                    <b-input type="text" v-model="validateEmail"></b-input>
                </b-field>
            </b-field>
        </section>

        <!-- Seleccionar cursos -->
        <br>
        <h2 class="subtitle">¿A qué programas desea inscribirse?</h2>
        <section class="container info">
            <button class="button is-medium is-primary" @click="alert">
                Ver horario de los programas
            </button>
            <hr>
            <div>
                <section class="columns">
                    <b-checkbox class="column" v-model="cbxHmw" false-value="no" true-value="yes">Club de Tareas
                    </b-checkbox>
                    <b-checkbox class="column" v-model="cbxChorus" false-value="no" true-value="yes">Coro Construye
                    </b-checkbox>
                    <b-checkbox class="column" v-model="cbxDance" false-value="no" true-value="yes">DANCO</b-checkbox>
                    <b-checkbox class="column" v-model="cbxOMIC" false-value="no" true-value="yes">OMIC</b-checkbox>
                </section>
                <section class="columns">
                    <b-checkbox class="column" v-model="cbxReal" false-value="no" true-value="yes">Real</b-checkbox>
                    <b-checkbox class="column" v-model="cbxSharing" false-value="no" true-value="yes">Sharing
                    </b-checkbox>
                    <b-checkbox class="column" v-model="cbxChess" false-value="no" true-value="yes">Ajedrez Construye
                    </b-checkbox>
                    <div class="column"></div>
                </section>
            </div>

        </section>
        <br>
        <!-- Botones para confirmar o cancelar -->
        <div class="buttons container is-centered">
            <b-button type="submit" size="is-medium" v-on:click="validate">Registrar</b-button>
            <b-button type="is-danger" size="is-medium">Cancelar</b-button>
        </div>
        <br>
    </section>
</template>

<script src="/__/firebase/7.6.2/firebase-firestore.js"></script>
<script>
import { db } from '../main'
    export default {
        name: 'Footer',
        firestore() {
            return {
                locations: db.collection('students').orderBy('createdAt')
            }
        },
        methods: {
            addLocation(name, image) { // <-- and here 
                const createdAt = new Date()
                
            },
            alert() {
                this.$buefy.dialog.alert({
                    title: 'Horario de Programas Privamera 2020',
                    message: '<img src="http://localhost:8080/img/horarioDummy.f8feae03.png" alt="Horario de prueba">',
                    confirmText: 'Ok'
                })
            },
            validate() {
                if (this.email !== this.validateEmail) {
                    this.validationEmails = "is-danger"
                    this.valmsg = "Los correos no son iguales"
                } else {
                    this.validationEmails = "null",
                        this.valmsg = ""
                }
                db.collection('students').add({
                    name:"dasda",
                    image: "dasda",
                    createdAt: "dsada"
                })
            }
        },
        data() {
            return {
                monthEs: ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre',
                    'Octubre', 'Noviembre', 'Diciembre'
                ],
                daysEs: ['Do', 'Lu', 'Ma', 'Mi', 'Ju', 'Vi', 'Sa'],
                yearsRange: [-30, 0],
                previous: null,
                studentName: null,
                studentFLN: null,
                studentMLN: null,
                birthDate: null,
                medicalInfo: null,
                grade: null,
                reads: null,
                tutorName: null,
                tutorFLN: null,
                tutorMLN: null,
                phone: null,
                email: null,
                validateEmail: null,
                //Checkbox'
                cbxHmw: null,
                cbxChorus: null,
                cbxDance: null,
                cbxOMIC: null,
                cbxReal: null,
                cbxSharing: null,

                validationEmails: null,
                valmsg: ""
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