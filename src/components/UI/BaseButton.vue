<template>
	<button :class="classList">
		<slot />
	</button>
</template>

<script>
import { computed } from 'vue';

export default {
	name: 'BaseButton',
	props: {
		type: {
			type: String,
			default: 'primary',
			validator(value) {
				return ['primary', 'icon'].includes(value);
			},
		},
	},
	setup(props) {
		const classList = computed(() => {
			const list = ['base-button'];

			if (props.type) {
				list.push(props.type);
			}

			return list;
		});
		return {
			classList,
		};
	},
};
</script>

<style lang="scss">
.base-button {
	cursor: pointer;
	background: none;
	border: none;

	&.primary {
	}

	&.icon {
	}
}
</style>
