<template>
	<div></div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
	setup() {
		const count = ref(0);
		const state = reactive({
			count,
		});
		// console.log(count.value);
		// console.log('sate.count:', state.count.value);

		// 배열
		const message = ref('Hello');
		const arr = reactive({ message });
		console.log(arr[0].value);

		return {};
	},
};
</script>

<style lang="scss" scoped></style>
