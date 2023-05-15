<template>
	<div class="card">
		<div v-if="$slots.header" class="card-header">
			<slot :header-message="headerMessage" name="header">#header</slot>
		</div>
		<div v-if="$slots.default" class="card-body">
			<slot :child-message="childMessage" :hello-message="helloMessage"
				>#body</slot
			>
		</div>
		<div v-if="hasFooter" class="card-footer text-body-secondary">
			<slot :footer-message="footerMessage" name="footer">#footer</slot>
		</div>
	</div>
</template>

<script>
import { computed } from 'vue';
import { ref } from 'vue';

export default {
	setup(props, { slots }) {
		const childMessage = ref('hello');
		const helloMessage = ref('hellow');
		const headerMessage = ref('header message');
		const footerMessage = ref('footer message');
		const hasFooter = computed(() => !slots.footer);
		return {
			childMessage,
			helloMessage,
			headerMessage,
			footerMessage,
			hasFooter,
		};
	},
};
</script>

<style lang="scss" scoped></style>
