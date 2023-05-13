<template>
	<p>{{ message }}</p>
	<button @click="increment"></button>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const message = ref('Hello vue');
		const increment = () => {
			message.value = message.value + 1;
		};
		return {
			message,
			increment,
		};
	},
};
</script>

<style lang="scss" scoped></style>
