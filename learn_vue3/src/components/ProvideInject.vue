<template>
	<div class="container py-4">
		<div class="card">
			<div class="card-header">Provide Inject</div>
			<div class="card-body">
				<button @click="count++">Click</button>
				<p>appMessage: {{ appMessage }}</p>
				<Child></Child>
			</div>
		</div>
	</div>
</template>

<script>
import { inject, provide, readonly, ref } from 'vue';
import Child from './Child.vue';
export default {
	components: {
		Child,
	},
	setup() {
		const staticMessage = 'static message';
		const message = ref('message');

		const updateMessage = appendMessage => {
			message.value = message.value + appendMessage;
		};
		const count = ref(10);

		// provide('static-message', staticMessage);
		provide('message', { message: readonly(message), updateMessage });
		provide('count', count);

		const appMessage = inject('app-message');

		return { count, appMessage };
	},
	mounted() {
		// 컴포넌트 인스턴스가 생성되고 나서야 this로 접근할 수 있다.
		// setup 에서는 this가 undefined -> provide 와 inject로 접근하면 된다.
		console.log('msg', this.msg);
	},
};
</script>

<style lang="scss" scoped></style>
