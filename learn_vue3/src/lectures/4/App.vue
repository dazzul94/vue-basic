<template>
	<div>
		<h2>반응형 메시지</h2>
		<p>{{ reactiveMessage }}</p>
		<button v-on:click="addReactiveMessage">Add Message</button>
		<h2>일반 메시지</h2>
		<p>{{ normalMessage }}</p>
		<button v-on:click="addNormalMessage">Add Message</button>
	</div>
</template>

<script>
import { onBeforeMount, onMounted, ref } from 'vue';

export default {
	setup() {
		const reactiveMessage = ref('Hello Reactive Messages');
		const addReactiveMessage = () => {
			reactiveMessage.value = reactiveMessage.value + '!';
		};

		let normalMessage = 'Normal Message';
		const addNormalMessage = () => {
			normalMessage = normalMessage + '!';
		};

		onMounted(() => {
			console.log('onMounted');
		});

		onBeforeMount(() => {
			console.log('onBeforMount');
		});
		return {
			reactiveMessage,
			normalMessage,
			addReactiveMessage,
			addNormalMessage,
		};
	},
};
</script>

<style lang="scss" scoped></style>
