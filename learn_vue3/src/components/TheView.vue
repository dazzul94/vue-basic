<template>
	<main class="container py-4">
		<TemplateRef></TemplateRef>
	</main>
</template>

<script>
import TemplateRef from './TemplateRef.vue';
export default {
	components: {
		TemplateRef,
	},
	setup() {
		return {};
	},
};
</script>

<style lang="scss" scoped></style>
