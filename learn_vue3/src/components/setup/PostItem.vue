<template>
	<div class="card">
		<div class="card-body">
			<!-- type : news, notice -->
			<span class="badge bg-secondary">{{ typeName }}</span>
			<h5 class="card-title red mt-2">{{ title }}</h5>
			<p class="card-text">
				{{ contents }}
			</p>
			<a @click="toggleLike" href="#" class="btn" :class="isLikeClass"
				>좋아요</a
			>
		</div>
	</div>
</template>
<!-- 한번만 실행 -->
<script>
console.log('normal script setup');
</script>

<script setup>
import { computed } from 'vue';
console.log('script setup');

const props = defineProps({
	type: {
		type: String,
		default: 'news',
		validator: value => {
			return ['news', 'notice'].includes(value);
		},
	},
	title: {
		type: String,
		required: true,
	},
	contents: {
		type: String,
		// required: true,
	},
	isLike: {
		type: Boolean,
		default: false,
	},
	obj: {
		type: Object,
		default: () => {},
	},
});

const emit = defineEmits(['toggleLike']);
const isLikeClass = computed(() =>
	props.isLike ? 'btn-danger' : 'btn-outline-danger',
);
const typeName = computed(() => (props.type === 'news' ? '뉴스' : '공지사항'));
const toggleLike = () => {
	// props.isLike = !props.isLike;
	emit('toggleLike');
};
</script>
