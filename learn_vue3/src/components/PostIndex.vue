<template>
	<main>
		<div class="container py-4">
			<PostCreate @create-post="createPost"></PostCreate>
			<hr class="my-4" />
			<div class="row g-3">
				<div v-for="post in posts" :key="post.id" class="col col-4">
					<AppCard
						:title="post.title"
						:contents="post.contents"
						:is-like="post.isLike"
						:type="post.type"
						@toggle-like="post.isLike = !post.isLike"
					></AppCard>
				</div>
			</div>

			<hr class="my-4" />
			<LabelInput
				v-model="username"
				label="이름"
				class="parent-class"
				style="color: red"
				id="parent_id"
			></LabelInput>
		</div>
	</main>
</template>

<script>
import { reactive, ref } from 'vue';
import AppCard from './PostItem.vue';
import PostCreate from './PostCreate.vue';
import LabelInput from './LabelInput.vue';
import LabeTitle from './LabeTitle.vue';
import Username from './Username.vue';
export default {
	components: {
		AppCard,
		PostCreate,
		LabelInput,
	},
	setup() {
		const posts = reactive([
			{
				id: 1,
				title: '제목3',
				contents: '내용3',
				isLike: true,
				type: 'news',
			},
			{
				id: 2,
				title: '제목4',
				contents: '내용4',
				isLike: false,
				type: 'notice',
			},
			{
				id: 3,
				title: '제목5',
				contents: '내용5',
				isLike: false,
				type: 'news',
			},
			{
				id: 4,
				title: '제목6',
				contents: '내용6',
				isLike: true,
				type: 'notice',
			},
		]);
		const createPost = newPost => {
			posts.push(newPost);
		};

		const username = ref('');
		const firstname = ref('');
		const lastname = ref('');
		return { posts, createPost, username, firstname, lastname };
	},
};
</script>
