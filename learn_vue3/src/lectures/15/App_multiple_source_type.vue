<template>
	<div></div>
</template>

<script>
import { reactive, ref, watch } from 'vue';

export default {
	setup() {
		const x = ref(0);
		const y = ref(0);

		const obj = reactive({
			count: 0,
		});

		const person = reactive({
			name: '홍길동',
			age: 30,
			hobby: '운동',
			obj: {
				count: 0,
			},
		});

		// watch(
		// 	() => x.value + y.value,
		// 	(sum, oldValue) => {
		// 		console.log('sum: ' + sum);
		// 		console.log('oldValue: ' + oldValue);
		// 	},
		// );

		watch([x, y], ([newX, newY], [oldX, oldY]) => {
			console.log('newX:' + newX + 'newY:' + newY);
			console.log('oldX:' + oldX + 'oldY:' + oldY);
		});

		// watch(
		// 	() => obj.count,
		// 	(newValue, oldValue) => {
		// 		console.log('newValue: ' + newValue);
		// 	},
		// );
		watch(obj, (newValue, oldValue) => {
			console.log('newValue: ' + newValue); // 같은 값
		});
		watch(person, newValue => {
			console.log('newValue:' + newValue);
		});
		return { x, y, obj };
	},
};
</script>

<style lang="scss" scoped></style>
