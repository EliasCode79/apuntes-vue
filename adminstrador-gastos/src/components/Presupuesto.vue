<script setup>
import { ref } from 'vue';
import Alerta from './Alerta.vue';
const presupuesto = ref(0);
const error = ref(0);

const definirPresupuesto = () => {
	if (presupuesto.value <= 0 || presupuesto.value === '') {
		error.value = 'presupuesto no valido';
		setTimeout(() => {
			error.value = '';
		}, 2000);
		return;
	}
	emit('definir-presupuesto', presupuesto.value);
};

const emit = defineEmits(['definir-presupuesto']);
</script>
<template>
	<form class="presupuesto" @submit.prevent="definirPresupuesto">
		<Alerta v-if="error">
			<p>{{ error }}</p>
		</Alerta>

		<div class="campo">
			<label for="nuevo-presupuesto">Definir presupuesto</label>
			<input
				v-model.number="presupuesto"
				id="nuevo-presupuesto"
				class="nuevo-presupuesto"
				placeholder="Añade un presupuesto"
				type="number"
				min="1"
			/>
		</div>
		<input type="submit" value="Definir presupuesto" />
	</form>
</template>
<style scoped>
.presupuesto {
	width: 100%;
}
.campo {
	display: grid;
	gap: 2rem;
}
.presupuesto label {
	font-size: 2.2rem;
	color: var(--azul);
	text-align: center;
}
.presupuesto input[type='number'] {
	background-color: var(--gris-claro);
	border-radius: 1rem;
	padding: 1rem;
	border: none;
	font-size: 2.2rem;
	text-align: center;
}
.presupuesto input[type='submit'] {
	background-color: var(--azul);
	border: none;
	padding: 1rem;
	text-align: center;
	font-size: 2rem;
	margin-top: 2rem;
	color: var(--blanco);
	font-weight: 900;
	width: 100%;
	transition: background-color 300ms ease;
}

.presupuesto input[type='submit']:hover {
	background-color: #1048a4;
	cursor: pointer;
}
</style>
