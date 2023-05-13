<template>
	<div>
		<button @click="counter += 1">Counter : {{ counter }}</button>
		<button @click="printEventInfo('Hello world', $event)">
			Inline Event Handler
		</button>
		<hr />
		<input type="text" @keyup="onKeyupHandler" />
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const counter = ref(0);
		const printEventInfo = (message, event) => {
			console.log('message:' + message);
			console.log('event.target:' + event.target);
			console.log('event.target.tagName:' + event.target.tagName);
		};
		const onKeyupHandler = event => {
			console.log('event.key:' + event.key);
		};
		return { counter, printEventInfo, onKeyupHandler };
	},
};
</script>

<style lang="scss" scoped></style>
