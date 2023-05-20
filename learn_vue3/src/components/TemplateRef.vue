<template>
	<div class="container py-4">
		<input ref="input" type="text" />
		<p>{{ input }}</p>
		<p v-if="input">
			{{ input.value }}, {{ $refs.input.value }}, {{ $refs.input == input }}
		</p>
		<ul>
			<li
				v-for="fruit in fruits"
				:key="fruit"
				:ref="el => itemRefs.push(el.textContent)"
			>
				{{ fruit }}
			</li>
		</ul>
		<hr />
		<TemplateRefChild ref="child"></TemplateRefChild>
	</div>
</template>

<script>
import { onMounted, ref } from 'vue';
import TemplateRefChild from './TemplateRefChild.vue';

export default {
	components: {
		TemplateRefChild,
	},
	setup() {
		const input = ref(null);
		console.log('setup', input.value);
		onMounted(() => {
			input.value.value = 'hello world';
			console.log('onMounted', input.value);
			// itemRefs.value.forEach(item => console.log('item:', item.textContent));
			itemRefs.value.forEach(item => console.log('item:', item));
			console.log('child message: ', child.value.message);
			child.value.sayHello();
		});
		const fruits = ref(['사과', '딸기', '포도']);
		const itemRefs = ref([]);
		const child = ref(null);

		return { input, fruits, itemRefs, child };
	},
};
</script>

<style lang="scss" scoped></style>
