<template>
	<div>
		<p>{{ message }}</p>
		<p>{{ reverseMessage }}</p>
	</div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
	setup() {
		const message = ref('Hello Vue3');
		const reverseMessage = ref('');

		const reverseFunction = () => {
			reverseMessage.value = message.value.split('').reverse().join('');
		};
		watch(message, reverseFunction);
		reverseFunction(message.value);
		return { message, reverseMessage };
	},
};
</script>

<style lang="scss" scoped></style>
