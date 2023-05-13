<template>
	<div>
		<ul>
			<template v-for="(item, index) in evenItems" :key="item.id">
				<!-- <li v-if="item.id % 2 === 0"> -->
				<li>ID: {{ item.id }} 인덱스: {{ index }}, {{ item.message }}</li>
				<!-- </li> -->
			</template>
		</ul>
		<ul v-for="(value, key, index) in myObject" :key="key">
			<li>{{ index }}-{{ key }}-{{ value }}</li>
		</ul>
	</div>
</template>

<script>
import { computed } from 'vue';
import { reactive } from 'vue';

export default {
	setup() {
		const items = reactive([
			{ id: 1, message: 'Java' },
			{ id: 2, message: 'Javascript' },
			{ id: 3, message: 'Vue3' },
			{ id: 4, message: 'HTML' },
		]);
		const evenItems = computed(() => items.filter(item => item.id % 2 === 0));

		const myObject = reactive({
			title: '제목',
			author: '홍길동',
			publishAt: '20160101',
		});
		return { items, evenItems, myObject };
	},
};
</script>

<style lang="scss" scoped></style>
