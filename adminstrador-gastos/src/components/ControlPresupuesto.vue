<script setup>
import image from '../assets/img/grafico.jpg';
</script>
<template>
	<div class="dos-columnas">
		<div class="contenedor-grafico">
			<img :src="image" />
		</div>
		<div class="contendor-presupuesto">
			<button class="reset-app">Reset App</button>
			<p><span>Presupuesto: </span>$0</p>
			<p><span>Disponible: </span>$0</p>
			<p><span>Gastado: </span>$0</p>
		</div>
	</div>
</template>
<style scoped></style>
