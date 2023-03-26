<template>
	<svg class="icon stop" :width="size" :height="size" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
		<rect width="20" height="20" :fill="fill"/>
	</svg>

</template>

<script setup>
defineProps({
	fill: {
		type: String,
		default: '#9E9E9E',
	},
	size: {
		type: Number,
		default: 20,
	},
});
</script>
