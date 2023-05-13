<template>
	<div>
		<p>{{ msg }}</p>
		<p v-text="msg"></p>
		<p v-html="html"></p>
		<p v-text="html"></p>
		<p v-once>{{ msg }}</p>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const msg = ref('안녕하세요');
		const html = ref('<strong>안녕</strong>');
		return { msg, html };
	},
};
</script>

<style lang="scss" scoped></style>
