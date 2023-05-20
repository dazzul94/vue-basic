<template>
	<div>{{ $parent }}</div>
	<ul>
		<li v-for="fruit in $parent.fruits" :key="fruit">{{ fruit }}</li>
	</ul>
</template>

<script setup>
import { ref } from 'vue';

const message = ref('hello');
const sayHello = () => {
	alert(message.value);
};
defineExpose({
	message,
	sayHello,
});
</script>

<style lang="scss" scoped></style>
