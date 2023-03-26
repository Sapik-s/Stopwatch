<template>
	<svg class="icon play" :width="size" :height="size" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
		<rect x="8.5" width="3" height="20" :fill="fill"/>
		<rect y="11.5" width="3" height="20" transform="rotate(-90 0 11.5)" :fill="fill"/>
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
