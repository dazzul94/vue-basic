<template>
	<div>
		<p>{{ message.value }}</p>
		<button v-on:click="addMessage">add click</button>
	</div>
</template>

<script>
import { reactive } from 'vue';

export default {
	setup() {
		let message = reactive({
			value: 'Hello world',
		});
		const addMessage = () => {
			message.value = message.value + '!';
		};

		return {
			message,
			addMessage,
		};
	},
};
</script>

<style lang="scss" scoped></style>
