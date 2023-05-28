<template>
	<div class="app-alert">
		<TransitionGroup name="slide">
			<div
				v-for="({ message, type }, index) in items"
				:key="index"
				class="alert"
				:class="typeStyle(type)"
				role="alert"
			>
				{{ message }}
			</div>
		</TransitionGroup>
	</div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
	items: Array,
});
const typeStyle = type =>
	props.type === 'error' ? 'alert-danger' : 'alert-primary';
</script>

<style scoped>
.app-alert {
	position: fixed;
	top: 10px;
	right: 10px;
}

.slide-enter-from {
	opacity: 0;
	transform: translateY(-30px);
}
.slide-enter-active {
	transition: all 0.5s ease;
}
.slide-enter-to {
	opacity: 1;
	transform: translateY(0px);
}
.slide-leave-from {
	opacity: 1;
	transform: translateY(0px);
}
.slide-leave-to {
	opacity: 0;
	transform: translateY(-30px);
}
.slide-leave-active {
	transition: all 0.5s ease;
}
</style>
