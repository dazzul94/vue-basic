<template>
	<AppModal v-model="show" title="게시글">
		<template #default>
			<div class="row">
				<div class="col-3">제목</div>
				<div class="col-9">{{ title }}</div>
				<div class="col-3">내용</div>
				<div class="col-9">{{ content }}</div>
				<div class="col-3">등록일</div>
				<div class="col-9">{{ createdAt }}</div>
			</div>
		</template>
		<template #actions>
			<button
				type="button"
				class="btn btn-secondary"
				data-bs-dismiss="modal"
				@click="closeModal"
			>
				Close
			</button>
		</template>
	</AppModal>
</template>

<script setup>
import AppModal from '@/components/AppModal.vue';
import { computed } from 'vue';
const props = defineProps({
	modelValue: Boolean,
	title: String,
	content: String,
	createdAt: [String, Number],
});
const emit = defineEmits(['update:modelValue']);
const show = computed({
	get() {
		return props.modelValue;
	},
	set(value) {
		emit('update:modelValue', value);
	},
});
const closeModal = () => (show.value = false);
</script>

<style lang="scss" scoped></style>
