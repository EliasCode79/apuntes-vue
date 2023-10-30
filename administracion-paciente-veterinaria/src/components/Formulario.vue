<script setup>
import { reactive } from 'vue';
import Alerta from './Alerta.vue';

const alerta = reactive({
	mensaje: '',
	tipo: '',
});

const paciente = reactive({
	nombre: '',
	propietario: '',
	email: '',
	alta: '',
	sintomas: '',
});

const validar = () => {
	if (Object.values(paciente).includes('')) {
		alerta.mensaje = 'Todos los campos son obligatorios';
		alerta.tipo = 'error';
		return;
	}

	console.log('Agregando pacientes');
};
</script>
<template>
	<div class="md:w-1/2">
		<h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>

		<p class="text-lg mt-5 text-center mb-10">
			Añade pacientes y <span class="text-indigo-600 font-bold">administralos</span>
		</p>

		<Alerta v-if="alerta.mensaje" :alerta="alerta" />

		<form class="bg-white shadow-md rounded-lg py-10 px-5 mb-10" @submit.prevent="validar">
			<div class="mb-5">
				<label for="mascota" class="block text-gray-700 uppercase font-bold">Nombre Mascota</label>
				<input
					class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
					id="mascota"
					type="text"
					placeholder="Nombre de la mascota"
					v-model="paciente.nombre"
				/>
			</div>
			<div class="mb-5">
				<label for="propietario" class="block text-gray-700 uppercase font-bold">Nombre Propietario</label>
				<input
					class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
					id="propietario"
					type="text"
					placeholder="Nombre del Propietario"
					v-model="paciente.propietario"
				/>
			</div>
			<div class="mb-5">
				<label for="email" class="block text-gray-700 uppercase font-bold">Email</label>
				<input
					class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
					id="email"
					type="email"
					placeholder="Email"
					v-model="paciente.email"
				/>
			</div>
			<div class="mb-5">
				<label for="alta" class="block text-gray-700 uppercase font-bold">Alta</label>
				<input
					v-model="paciente.alta"
					class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
					id="alta"
					type="date"
				/>
			</div>
			<div class="mb-5">
				<label for="sintomas" class="block text-gray-700 uppercase font-bold">Sintomas</label>
				<textarea
					v-model="paciente.sintomas"
					class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
					id="sintomas"
					type="text"
					placeholder="Describe los sintomas"
				/>
			</div>

			<input
				type="submit"
				class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-800 cursor-pointer transition-colors"
				value="Registrar Paciente"
			/>
		</form>
	</div>
</template>
