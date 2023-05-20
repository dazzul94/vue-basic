<template>
	<div class="p-3 bg-danger">
		<button class="btn btn-primary" type="button">
			MyButton {{ message }}
		</button>
	</div>
</template>

<script>
export default {
	inheritAttrs: false,
};
</script>
<script setup>
import { ref } from 'vue';
const message = ref('message');
</script>

<style lang="scss" scoped></style>
