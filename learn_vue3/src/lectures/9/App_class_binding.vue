<template>
	<div>
		<div class="text" :class="classObject">텍스트입니다.</div>
		<button @click="toggle">toggle</button>
		<button @click="hasError = !hasError">toggleError</button>
	</div>
</template>

<script>
import { computed } from 'vue';
import { reactive, ref } from 'vue';

export default {
	setup() {
		const isActive = ref(true);
		const hasError = ref(false);
		// const classObject = reactive({
		// 	active: true,
		// 	'text-danger': true,
		// });
		const classObject = computed(() => {
			return {
				active: true && true,
				'text-danger': true && true,
			};
		});

		const toggle = () => {
			isActive.value = !isActive.value;
		};
		return { isActive, toggle, hasError, classObject };
	},
};
</script>

<style scoped>
.active {
	font-weight: 900;
}
.text-danger {
	color: red;
}
</style>
