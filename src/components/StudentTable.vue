<template>
	<section>
		<b-table :data="students" :loading="loadingData" ref="table" paginated per-page="5"
			:opened-detailed="defaultOpenedDetails" detailed detail-key="studentName" :show-detail-icon="showDetailIcon"
			aria-next-label="Next page" aria-previous-label="Previous page" aria-page-label="Page"
			aria-current-label="Current page">
			<template slot-scope="studentData">
				<b-table-column label="Nombre" sortable>
					{{ studentData.row.studentName.concat(" ", studentData.row.studentFLN, " ", studentData.row.studentMLN).toString()}}
				</b-table-column>
				<b-table-column label="Tutor" sortable>
					{{ studentData.row.tutorName.concat(" ", studentData.row.tutorFLN, " ", studentData.row.tutorMLN) }}</b-table-column>
				<b-table-column label="Contacto" sortable>{{ studentData.row.email}}</b-table-column>
			</template>

			<template slot="detail" slot-scope="studentData">
				<b-field grouped group-multiline>
					<b-field label="Nombre" :label-position="labelPosition" expanded>
						<b-input :value=studentData.row.studentName></b-input>
					</b-field>

					<b-field label="Apellido Materno" :label-position="labelPosition" expanded>
						<b-input :value=studentData.row.studentFLN></b-input>
					</b-field>

					<b-field label="Apellido Paterno" :label-position="labelPosition" expanded>
						<b-input :value=studentData.row.studentMLN></b-input>

					</b-field>
				</b-field>
				<div class="buttons">
					<b-button type="is-info" @click="updateStudent(studentData.row)">Guardar cambios</b-button>
					<b-button type="is-danger">Cancelar</b-button>
				</div>

			</template>
		</b-table>
	</section>
</template>

<script src="/__/firebase/7.6.2/firebase-firestore.js"></script>
<script>
	import {
		db
	} from "../main";
	import {
		read
	} from "fs";

	export default {
		name: "StudentTable",
		data() {
			return {
				students: [],
				defaultOpenedDetails: [1],
				showDetailIcon: true,
				loadingData: false,
				labelPosition: 'on-border'
			};
		},
		async mounted() {
			try {
				this.loadingData = true;
				const students = await db.collection("students").get();
				students.forEach(student => {
					this.students.push(student.data());
				});
			} catch (error) {
				console.error(error);
			} finally {
				this.loadingData = false;
				console.log(this.students);
			}
		},
		methods: {
			updateStudent(row){
				alert(row.studentName);
			}
		}
	};
</script>

<style>
</style>