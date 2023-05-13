<template>
	<main>
		<div class="container py-4">
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
		</div>
	</main>
</template>

<script>
import { reactive } from 'vue';
import AppCard from './AppCard.vue';
export default {
	components: {
		AppCard,
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
		return { posts };
	},
};
</script>
