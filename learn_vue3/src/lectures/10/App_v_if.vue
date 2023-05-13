<template>
	<div>
		<h1 v-if="visible">Hello world</h1>
		<h1 v-else>false 입니다.</h1>
		<button @click="visible = !visible">toggle</button>
		<hr />
		<button @click="type = 'A'">A</button>
		<button @click="type = 'B'">B</button>
		<button @click="type = 'C'">C</button>
		<button @click="type = 'D'">D</button>

		<h1 v-if="type === 'A'">A입니다.</h1>
		<h1 v-else-if="type === 'B'">B입니다.</h1>
		<h1 v-else-if="type === 'C'">C입니다.</h1>
		<h1 v-else>A, B, C가 아닙니다.</h1>
		<hr />
		<template v-if="visible">
			<h1>Title</h1>
			<p>Paragraph</p>
			<p>Paragraph</p>
			<p>Paragraph</p>
			<p>Paragraph</p>
		</template>
		<hr />
		<h1 v-show="ok">Title 입니다.</h1>
		<button @click="ok = !ok">show toggle</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const visible = ref(true);
		const type = ref('A');
		const ok = ref(true);
		return { visible, type, ok };
	},
};
</script>

<style lang="scss" scoped></style>
