<template>
    <section>
        <!-- <b-tabs>
            <b-tab-item label="Alumnos registrados">
                <b-table :data="datos" :columns="columns" :loading="loadingData" focusable>
                </b-table>
            </b-tab-item>
        </b-tabs> -->
        <!-- <p>LOOL {{ datos }}</p> -->

        <b-table :data="datos" :loading="loadingData" ref="table" paginated per-page="5"
            :opened-detailed="defaultOpenedDetails" detailed detail-key="studentName"
            @details-open="(row, index) => $buefy.toast.open(`Expanded ${row.studentName}`)"
            :show-detail-icon="showDetailIcon" aria-next-label="Next page" aria-previous-label="Previous page"
            aria-page-label="Page" aria-current-label="Current page">

            <template slot-scope="props">
                <b-table-column label="Nombre" sortable>
                    {{ props.row.studentName + " " + props.row.studentFLN + ' ' + props.row.studentMLN }}
                </b-table-column>
                <b-table-column label="Tutor" sortable>
                    {{ props.row.tutorName + " " + props.row.tutorFLN + ' ' + props.row.tutorMLN }}
                </b-table-column>
                <b-table-column label="Contacto" sortable>
                    {{ props.row.email }}
                </b-table-column>

            </template>

            <template slot="detail" slot-scope="props">
                <article class="media">
                    <figure class="media-left">
                    </figure>
                    <div class="media-content">
                        <div class="content">
                            <div class="columns">
                                <div class="column box">
                                    <p>{{ props.row.studentName }} {{ props.row.studentFLN }} {{props.row.studentMLN}}</p>
                                    <p>{{ props.row.activities }}</p>
                                </div>
                                <div class="column box  ">

                                </div>
                            </div>
                        </div>
                    </div>
                </article>
            </template>
        </b-table>

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
        name: 'StudentTable',
        data() {
            return {
                datos: [],
                defaultOpenedDetails: [1],
                showDetailIcon: true,
                loadingData: false,
            }
        },
        async mounted() {
            try {
                this.loadingData = true
                const students = await db.collection("students").get()
                students.forEach(student => {
                    this.datos.push(student.data())
                })
            } catch (error) {
                console.error(error)
            } finally {
                this.loadingData = false
                console.log(this.datos)
            }
        },
        methods: {
            toggle(row) {
                this.$refs.table.toggleDetails(row)
            }
        }
    }
</script>

<style>

</style>