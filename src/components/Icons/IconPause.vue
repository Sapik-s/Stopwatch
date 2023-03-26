<template>
	<svg class="icon pause" :width="size" :height="size" viewBox="0 0 10 20" fill="none" xmlns="http://www.w3.org/2000/svg">
		<rect x="7" width="3" height="20" :fill="fill"/>
		<rect width="3" height="20" :fill="fill"/>
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
