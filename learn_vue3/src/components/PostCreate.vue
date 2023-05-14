<template>
	<div class="row g-3">
		<div class="col col-2">
			<select
				v-model="type"
				class="form-select"
				aria-label="Default select example"
			>
				<option value="news">뉴스</option>
				<option value="notice">공지사항</option>
			</select>
		</div>
		<div class="col col-8">
			<input type="text" class="form-control" v-model="title" />
		</div>
		<div class="col col-2 d-grid">
			<button @click="createPost" class="btn btn-primary">추가</button>
		</div>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	// emits: ['createPost'],
	emits: {
		createPost: newPost => {
			if (!newPost.title) {
				return false;
			} else if (!newPost.type) {
				return false;
			}
			return true;
		},
	},
	setup(props, { emit }) {
		const type = ref('news');
		// context.emit
		const title = ref('');
		const createPost = () => {
			const newPost = {
				title: title.value,
				type: type.value,
			};
			emit('createPost', newPost);
			type.value = 'news';
			title.value = '';
		};
		return { createPost, title, type };
	},
};
</script>

<style lang="scss" scoped></style>
