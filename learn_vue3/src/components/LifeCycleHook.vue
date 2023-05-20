<template>
	<div class="container py-4">
		<input ref="inputRef" type="text" value="hello world!" />
		<button @click="visible = !visible">Toggle child</button>
		<LifeCycleChild v-if="visible"></LifeCycleChild>
		<p id="message">{{ message }}</p>
	</div>
</template>

<script>
import { onBeforeMount, onBeforeUpdate, onMounted, onUpdated, ref } from 'vue';
import LifeCycleChild from './LifeCycleChild.vue';
export default {
	components: {
		LifeCycleChild,
	},
	setup() {
		// console.log('set up');
		const inputRef = ref(null);
		const message = ref('');
		const visible = ref(false);
		// onBeforeMount(() => {
		// 	console.log('onbefore mount', inputRef.value);
		// });
		// onMounted(() => {
		// 	console.log('onmounted', inputRef.value.value);
		// });
		// onBeforeUpdate(() => {
		// 	console.log('onBeforeUpdate', message.value);
		// 	console.log('domcontent', document.querySelector('message').textContent);
		// });
		// onUpdated(() => {
		// 	console.log('onupdated', message.value);
		// 	console.log('domcontent', document.querySelector('message').textContent);
		// });
		return { inputRef, message, visible };
	},
	// data: () => ({
	// 	dataMessage: 'data-message',
	// }),
	// beforeCreate() {
	// 	console.log('before create', this.dataMessage);
	// },
	// created() {
	// 	console.log('created', this.dataMessage);
	// },
};
</script>

<style lang="scss" scoped></style>
