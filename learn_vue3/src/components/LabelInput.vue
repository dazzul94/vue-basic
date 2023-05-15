<template>
	<label class="form_label" id="child_id">
		{{ label }}
	</label>
	<input type="text" v-model="value" v-bind="$attrs" class="form_control" />
</template>

<script>
import { computed } from 'vue';
import { ref } from 'vue';

export default {
	props: ['modelValue', 'label'],
	emits: ['update:modelValue'],
	setup(props, { emit }) {
		const value = computed({
			get() {
				return props.modelValue;
			},
			set(value) {
				emit('update:modelValue', value);
			},
		});
		return { value };
	},
};
</script>

<style lang="scss" scoped></style>
