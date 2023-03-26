<template>
	<main>
		<div class="container">
			<div class="main-page">
				<Stopwatch v-for="item in counter" :key="item"/>
				<div class="main-page__add-block">
					<BaseButton type="icon" @click="onAddStopwatch">
						<IconPlus />
					</BaseButton>
				</div>
			</div>
		</div>
	</main>
</template>

<script setup>
import Stopwatch from '@/components/Stopwatch.vue';
import IconPlus from '@/components/Icons/IconPlus.vue';
import BaseButton from '@/components/UI/BaseButton.vue';
import { ref } from 'vue';

const counter = ref(1);

function onAddStopwatch() {
	counter.value++;
}
</script>

<style lang="scss">
.main-page {
	display: flex;
	flex-wrap: wrap;
	padding-top: 72px;

	&__add-block {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 225px;
		height: 120px;
		margin: 0 25px 45px 25px;
		background: #696969;
	}
}

.container {
	display: block;
	margin: 0 auto;
}

@media (min-width: 1024px) {
	.container {
		width: 840px;
	}
}

@media (min-width: 768px) and (max-width: 1023px) {
	.container {
		width: 500px;
	}
	.main-page {
		justify-content: space-between;
		flex-wrap: wrap;

		&__add-block {
			margin: 0 0 45px 0;
		}
	}
}

@media (min-width: 320px) and (max-width: 767px) {
	.container {
		width: 225px;
	}
	.main-page {
		flex-direction: column;

		&__add-block {
			margin: 0 0 45px 0;
		}
	}
}

</style>
