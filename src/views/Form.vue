<template>
    <section class="has-background-dark">
        <link rel="stylesheet" href="https://cdn.materialdesignicons.com/2.5.94/css/materialdesignicons.min.css">
        <section class="hero is-primary is-bold">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">
                        Registro de alumnos
                    </h1>
                </div>
            </div>
        </section>

        <br>
        <h2 class="subtitle">Información previa</h2>
        <section class="container info">
            <strong style="color: red" v-if="missingBIC">Seleccionar una opción</strong>
            <div class="block">
                <b-field label="¿El alumno ha estado inscrito en alguno de nuestros programas?" />
                <b-radio v-model="beenOnIC" native-value="true">
                    Sí
                </b-radio>
                <b-radio v-model="beenOnIC" native-value="false">
                    No
                </b-radio>
            </div>
        </section>

        <br>
        <h2 class="subtitle">Información del alumno</h2>
        <section class="container info has-text-centered">

            <!-- INFORMACION BASICA DEL ALUMNO -->
            <b-field grouped group-multiline>
                <b-field label="Nombre(s)" expanded :type="{ 'is-danger': nameError }"
                    :message="{ 'El campo no puede estar vacío': nameError}">
                    <b-input type="text" v-model="studentName" />
                </b-field>
                <b-field label="Apellido Paterno" expanded :type="{ 'is-danger': FLNError }"
                    :message="{ 'El campo no puede estar vacío': FLNError}">
                    <b-input type="text" v-model="studentFLN" />
                </b-field>
                <b-field label="Apellido Materno" expanded :type="{ 'is-danger': MLNError }"
                    :message="{ 'El campo no puede estar vacío': MLNError}">
                    <b-input type="text" v-model="studentMLN"></b-input>
                </b-field>
            </b-field>
            <b-field grouped group-multiline>
                <b-field label="Fecha de nacimiento" expanded :type="{ 'is-danger': birthDateError }"
                    :message="{ 'El campo no puede estar vacío': birthDateError}">
                    <b-datepicker :month-names="monthEs" :dayNames="daysEs" :years-range="yearsRange"
                        placeholder="Seleccionar fecha" icon="calendar-today" v-model="birthDate">
                    </b-datepicker>
                </b-field>
                <b-field label="Grado Escolar" expanded :type="{ 'is-danger': gradeError }"
                    :message="{ 'El campo no puede estar vacío': gradeError}">
                    <b-input type="text" v-model="grade"></b-input>
                </b-field>
                <div style="padding: 10px;">
                    <strong style="color: red" v-if="missingReading">Seleccionar una opción</strong>
                    <b-field label="¿Sabe leer?" expanded>
                        <div class="block">
                            <b-radio v-model="reads" native-value="true">
                                Sí
                            </b-radio>
                            <b-radio v-model="reads" native-value="false">
                                No
                            </b-radio>
                        </div>
                    </b-field>
                </div>
            </b-field>

            <!-- INFORMACIÓN ESCOLAR DEL ALUMNO -->

            <b-field label="Condiciones médicas y/o alergias" expanded>
                <b-input type="textarea" v-model="medicalInfo"></b-input>
            </b-field>
        </section>

        <!-- Información del tutor -->
        <br>
        <h2 class="subtitle">Información de padre, madre o tutor</h2>
        <section class="container info">
            <b-field grouped group-multiline>
                <b-field label="Nombre(s)" expanded :type="{ 'is-danger': tutorError }"
                    :message="{ 'El campo no puede estar vacío': tutorError}">
                    <b-input type="text" v-model="tutorName"></b-input>
                </b-field>
                <b-field label="Apellido Paterno" expanded :type="{ 'is-danger': tutorFLNError }"
                    :message="{ 'El campo no puede estar vacío': tutorFLNError}">
                    <b-input type="text" v-model="tutorFLN"></b-input>
                </b-field>
                <b-field label="Apellido Materno" expanded :type="{ 'is-danger': tutorMLNError }"
                    :message="{ 'El campo no puede estar vacío': tutorMLNError}">
                    <b-input type="text" v-model="tutorMLN"></b-input>
                </b-field>
            </b-field>

            <b-field grouped group-multiline>
                <b-field label="Teléfono" expanded :type="{ 'is-danger': phoneError }">
                    <b-input v-model="phone" minlength="7" validation-message="Introduce un teléfono valido"></b-input>
                </b-field>
                <b-field label="Correo Electrónico" expanded :type="{ 'is-danger': emailError }">
                    <b-input type="email" v-model="email" validation-message="Introduce un correo válido"></b-input>
                </b-field>
                <b-field label="Volver a escribir correo" expanded :type="{ 'is-danger': emailValError }"
                    :message="{ 'Los correos no coinciden': emailValError}">
                    <b-input type="email" v-model="validateEmail"></b-input>
                </b-field>
            </b-field>
        </section>

        <!-- Seleccionar cursos -->
        <br>
        <h2 class="subtitle">¿A qué programas desea inscribirse?</h2>
        <section class="container info">
            <div>
                <div class="columns">
                    <div class="column is-two-thirds">
                        <strong>Horarios Primavera 2020</strong>
                        <br>
                        <img src="../assets/horarioDummy.png" alt="Horario de actividades">
                    </div>
                    <section class="column">
                        <strong style="color: red;" v-if="missingAct">Seleccionar al menos una actividad</strong>
                        <hr>
                        <section style="display: flex; flex-direction: column;">
                            <b-checkbox class="checkbox" v-model="cbxHmw" false-value="no" true-value="Tareas">
                                Club de Tareas
                            </b-checkbox>
                            <b-checkbox class="checkbox" v-model="cbxChorus" false-value="no" true-value="Coro">
                                Coro Construye
                            </b-checkbox>
                            <b-checkbox class="checkbox" v-model="cbxDance" false-value="no" true-value="DANCO">
                                DANCO
                            </b-checkbox>
                            <b-checkbox class="checkbox" v-model="cbxOMIC" false-value="no" true-value="OMIC">
                                OMIC
                            </b-checkbox>
                            <b-checkbox class="checkbox" v-model="cbxReal" false-value="no" true-value="Real">
                                Real
                            </b-checkbox>
                            <b-checkbox class="checkbox" v-model="cbxSharing" false-value="no" true-value="Sharing">
                                Sharing
                            </b-checkbox>
                            <b-checkbox class="checkbox" v-model="cbxChess" false-value="no" true-value="Ajedrez">
                                Ajedrez Construye
                            </b-checkbox>
                        </section>
                    </section>
                </div>
            </div>
        </section>
        <br>
        <!-- Botones para confirmar o cancelar -->
        <div class="buttons container is-centered">
            <b-button class="has-text-weight-bold" type="is-success" size="is-medium"
                v-on:click="register(beenOnIC, studentName, studentFLN, studentMLN, birthDate, medicalInfo, grade, reads, tutorName, tutorFLN, tutorMLN, phone, email)">
                Registrar</b-button>
            <b-button type="is-danger" size="is-medium">
                <router-link to="/" class="has-text-white has-text-weight-bold">Cancelar</router-link>
            </b-button>
        </div>
        <br>
    </section>
</template>

<script src="/__/firebase/7.6.2/firebase-firestore.js"></script>
<script>
    import {
        db
    } from '../main'
    import {
        read
    } from 'fs'

    export default {
        name: 'Footer',
        data() {
            return {
                // Para el formato del datepicker
                monthEs: ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre',
                    'Octubre', 'Noviembre', 'Diciembre'
                ],
                daysEs: ['Do', 'Lu', 'Ma', 'Mi', 'Ju', 'Vi', 'Sa'],
                yearsRange: [-30, 0],

                //Datos del alumno
                beenOnIC: null,
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
                //Checkbox's
                cbxHmw: null,
                cbxChorus: null,
                cbxDance: null,
                cbxOMIC: null,
                cbxReal: null,
                cbxSharing: null,
                cbxChess: null,

                nameError: false,
                FLNError: false,
                MLNError: false,
                birthDateError: false,
                gradeError: false,
                tutorError: false,
                tutorFLNError: false,
                tutorMLNError: false,
                phoneError: false,
                emailError: false,
                emailValError: false,
                missingBIC: false,
                missingReading: false,
                missingAct: false,
                activities: null
            }
        },
        firestore() {
            return {
                locations: db.collection('students').orderBy('createdAt')
            }
        },
        methods: {
            missingDataAlert() {
                this.$buefy.dialog.alert({
                    title: 'Faltan campos por completar',
                    message: 'Revisar y completar los campos faltantes',
                    type: 'is-danger',
                })
            },
            failed() {
                this.$buefy.dialog.alert({
                    title: 'Error',
                    message: 'Hubo un error al procesar los datos, revisa tu conexión a internet o refresca la página',
                    type: 'is-danger',
                })
            },
            successAlert() {
                this.$buefy.dialog.alert({
                    title: 'Registro correcto',
                    message: 'El alumno fue registrado correctamente',
                    type: 'is-success',
                })
            },
            validate() {
                this.nameError = (this.studentName === null || this.studentName === '') ? true : false;
                this.FLNError = (this.studentFLN === null || this.studentFLN === '') ? true : false;
                this.MLNError = (this.studentMLN === null || this.studentMLN === '') ? true : false;
                this.birthDateError = (this.birthDate === null || this.birthDate === '') ? true : false;
                this.gradeError = (this.grade === null || this.grade === '') ? true : false;
                this.tutorError = (this.tutorName === null || this.tutorName === '') ? true : false;
                this.tutorFLNError = (this.tutorFLN === null || this.tutorFLN === '') ? true : false;
                this.tutorMLNError = (this.tutorMLN === null || this.tutorMLN === '') ? true : false;
                this.phoneError = (this.phone === null || this.phone === '') ? true : false;
                this.emailError = (this.email === null || this.email === '') ? true : false;
                this.emailValError = (this.validateEmail !== this.email || this.validateEmail === null) ? true : false;
                this.missingBIC = (this.beenOnIC === null) ? true : false;
                this.missingReading = (this.reads === null) ? true : false
                return !this.nameError && !this.FLNError && !this.MLNError && !this.birthDateError && !this
                    .gradeError && !this.tutorError && !this.tutorFLNError &&
                    !this.tutorMLNError && !this.phoneError && !this.emailError && !this.emailValError && !this
                    .missingBIC && !this.missingReading && !this.missingAct
            },
            register(beenOnIC, studentName, studentFLN, studentMLN, birthDate, medicalInfo, grade, reads, tutorName,
                tutorFLN, tutorMLN, phone, email) {
                let checks = [this.cbxHmw, this.cbxChorus, this.cbxDance, this.cbxOMIC, this.cbxReal, this.cbxSharing,
                    this.cbxChess
                ];
                let activities = checks.filter(check => (check !== null && check !== 'no'));
                console.log(activities);
                this.missingAct = (activities.length === 0);
                let formIsCompleted = this.validate();
                if (!formIsCompleted) {
                    console.log("Missing data")
                    this.missingDataAlert()
                } else {
                    try {
                        console.log("Data complete")
                        const createdAt = new Date()
                        beenOnIC = (beenOnIC === 'true')
                        reads = (reads === 'true')
                        db.collection('students').add({
                            beenOnIC,
                            studentName,
                            studentFLN,
                            studentMLN,
                            birthDate,
                            medicalInfo,
                            grade,
                            reads,
                            tutorName,
                            tutorFLN,
                            tutorMLN,
                            phone,
                            email,
                            createdAt,
                            activities
                        })
                    } catch (error) {
                        console.error(error);
                        this.failed()
                    }
                    this.successAlert()
                    this.$router.push('/')
                }
            }
        }
    }
</script>

<style scoped>
    .info {
        border: solid black 1px;
        padding: 15px;
    }

    .subtitle {
        font-weight: bold;
    }

    .checkbox {
        padding-top: 10%;
    }
</style>