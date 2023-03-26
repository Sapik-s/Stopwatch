<template>
	<div class="main">
		<div class="main__wrapper">
			<div class="main__item stopwatch" :class="{ 'is-play': isPlay}">
				<div class="stopwatch__time">
					<div class="time">{{ time }}</div>
				</div>
				<hr class="stopwatch__hr">
				<div class="stopwatch__bottom-item">
					<BaseButton class="stopwatch__btn play" type="icon" @click="onPlay" v-if="!isPlay">
						<IconPlay :fill="isPlay ? '#ffffff' : '#9E9E9E'"/>
					</BaseButton>

					<BaseButton class="stopwatch__btn pause" type="icon" @click="onPause" v-if="isPlay">
						<IconPause :fill="isPlay ? '#ffffff' : '#9E9E9E'"/>
					</BaseButton>

					<BaseButton class="stopwatch__btn" type="icon" @click="onStop">
						<IconStop :fill="isPlay ? '#ffffff' : '#9E9E9E'"/>
					</BaseButton>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
import IconPlay from '@/components/Icons/IconPlay.vue';
import BaseButton from '@/components/UI/BaseButton.vue';
import IconStop from '@/components/Icons/IconStop.vue';
import IconPause from '@/components/Icons/IconPause.vue';
import { ref, computed } from 'vue';

const counter = ref(0);
const timerId = ref(null);
const isPlay = ref(false);

const time = computed(() => {
	let hour = 0, minute = 0, seconds = 0;

	seconds = counter.value % 60;
	minute = Math.floor(counter.value / 60);
	if (minute / (hour * 60) >= 0) {
		minute = minute - (hour * 60);
	}

	hour = Math.floor(counter.value / 60 / 60);

	if (hour) {
		return `${twoDigits(hour)}:${twoDigits(minute)}:${twoDigits(seconds)}`;
	} else if (minute) {
		return `${twoDigits(minute)}:${twoDigits(seconds)}`;
	} else if (seconds) {
		return twoDigits(seconds);
	}

	return '00';
});

/**
 * Добавляет 0 к числу
 *
 * @param num
 * @returns {string}
 */
function twoDigits(num) {
	return ('0' + num).slice(-2);
}

/**
 * Запускаем счётчик
 */
function onPlay() {
	timerId.value = setInterval(() => {
		counter.value++;
	}, 1000);
	isPlay.value = true;
}

/**
 * Ставим счётчик на паузу
 */
function onPause() {
	clearInterval(timerId.value);
	isPlay.value = false;
}

/**
 * Сбрасываем счётчик до 0
 */
function onStop() {
	clearInterval(timerId.value);
	counter.value = 0;
	isPlay.value = false;
}

</script>

<style scoped lang="scss">
.main {
	&__wrapper {
		display: flex;
		flex-direction: column;
		width: 225px;
		height: 120px;
		margin: 0 25px 45px 25px;
		background: #696969;
	}
}

.stopwatch {
	padding: 20px 0;

	&__time {
		display: flex;
		justify-content: center;
		font-style: normal;
		font-weight: 400;
		font-size: 22px;
		line-height: 21px;
		color: #9E9E9E;
	}

	&__bottom-item {
		display: flex;
		justify-content: center;
	}

	&__btn {
		padding: 0 24px;
	}

	&__hr {
		margin: 20px 0;
		border: 1px solid #9E9E9E;
	}
}

.is-play {
	.time {
		color: #FFFFFF;
	}

	.stopwatch__hr {
		border-color: #FFFFFF;
	}

	.isActive{
		fill: #FFFFFF;
	}
}


@media (min-width: 768px) and (max-width: 1023px) {
	.main {
		&__wrapper {
			margin: 0 0 45px 0;
		}
	}
}

@media (min-width: 320px) and (max-width: 767px) {
	.main {
		&__wrapper {
			margin: 0 0 45px 0px;
		}

	}
}
</style>
