<template>
	<div>
		<div :style="styleObject">
			Lorem ipsum dolor sit amet consectetur, adipisicing elit. Molestias
			repellat, repudiandae odit voluptates corporis eligendi eius praesentium
			optio voluptas, omnis consectetur dolore possimus molestiae a.
			Voluptatibus itaque ex esse inventore.
		</div>
		<button @click="fontSize++">+</button>
		<button @click="fontSize--">-</button>
	</div>
</template>

<script>
import { computed } from 'vue';
import { reactive, ref } from 'vue';

export default {
	setup() {
		// const styleObject = reactive({
		// 	color: 'red',
		// 	fontSize: '13px',
		// });
		const fontSize = ref(13);
		const styleObject = computed(() => {
			return {
				color: 'red',
				fontSize: fontSize.value + 'px',
			};
		});
		return { styleObject, fontSize };
	},
};
</script>

<style lang="scss" scoped></style>
