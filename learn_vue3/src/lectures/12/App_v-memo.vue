<template>
	<div v-memo="[subscribers]">
		<p>subscribers: {{ subscribers }}</p>
		<p>views: {{ views }}</p>
		<p>likes: {{ likes }}</p>
		<button @click="subscribers++">subs++</button>
		<button @click="views++">views++</button>
		<button @click="likes++">likes++ s</button>
	</div>
	<div>
		<p>subscribers: {{ subscribers }}</p>
		<p>views: {{ views }}</p>
		<p>likes: {{ likes }}</p>
		<button @click="subscribers++">subs++</button>
		<button @click="views++">views++</button>
		<button @click="likes++">likes++ s</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const subscribers = ref(400);
		const views = ref(400);
		const likes = ref(20);
		return { subscribers, views, likes };
	},
};
</script>

<style lang="scss" scoped></style>
