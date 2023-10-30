<script setup>
import { ref, reactive } from 'vue';
import Header from './components/Header.vue';
import Formulario from './components/Formulario.vue';
import Paciente from './components/Paciente.vue';

const pacientes = ref([]);

const paciente = reactive({
	nombre: '',
	propietario: '',
	email: '',
	alta: '',
	sintomas: '',
});

const guardarPaciente = () => {
	// utilizamos el operador spread para copiar el objeto paciente y agregar al arreglo reactivo, si lo enviamos directamente como paciente(variable reactiva) vemos despues q sus valores cambia y esto hara q el objeto q esta en el arrelgo cambie su valor. El operador spreed hace un copia exacta del objeto paciente, y si se llega a modicar este no afectara a la variable reactiva paciente.
	pacientes.value.push({ ...paciente });

	// Reiniciar el objeto
	paciente.nombre = '';
	paciente.propietario = '';
	paciente.email = '';
	paciente.alta = '';
	paciente.sintomas = '';

	// otra forma de reinicar el objeto
	// Object.assign(paciente, {
	// 	nombre: '',
	// 	propietario: '',
	// 	email: '',
	// 	alta: '',
	// 	sintomas: '',
	// });
};
</script>
<template>
	<div class="container mx-auto mt-20">
		<Header />
		<div class="mt-12 md:flex mx-auto">
			<!-- Formulario con multiples v-models -->
			<Formulario
				v-model:nombre="paciente.nombre"
				v-model:propietario="paciente.propietario"
				v-model:email="paciente.email"
				v-model:alta="paciente.alta"
				v-model:sintomas="paciente.sintomas"
				@guardar-paciente="guardarPaciente"
			/>
			<div class="md:w-1/2 md:h-screen overflow-y-scroll">
				<h3 class="font-black text-3xl text-center">Administra tus pacientes</h3>
				<div v-if="pacientes.length > 0" class="">
					<p class="text-lg mt-5 text-center mb-10">
						Informacion de <span class="text-indigo-600 font-bold">Pacientes</span>
					</p>
					<Paciente v-for="paciente in pacientes" :paciente="paciente" />
				</div>

				<div v-else class="mt-10 text-2xl text-center">No hay pacientes</div>
			</div>
		</div>
	</div>
</template>
