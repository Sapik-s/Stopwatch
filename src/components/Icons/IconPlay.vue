<template>
	<svg class="icon play" :width="size" :height="size" viewBox="0 0 17 20" fill="none"
		 xmlns="http://www.w3.org/2000/svg">
		<path d="M0 20V0L17 10L0 20Z" :fill="fill" />
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
