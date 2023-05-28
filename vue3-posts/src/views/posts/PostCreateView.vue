<template>
	<div>
		<h2>게시글 등록</h2>
		<hr class="my-4" />
		<PostForm
			v-model:title="form.title"
			v-model:content="form.content"
			@submit.prevent="save"
		>
			<template #actions>
				<button
					type="button"
					class="btn btn-outline-dark me-2"
					@click="goListPage"
				>
					목록
				</button>
				<button class="btn btn-outline-primary">저장</button>
			</template>
		</PostForm>
	</div>
</template>

<script setup>
import { createPost } from '@/api/posts';
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import PostForm from './PostForm.vue';
const router = useRouter();

const form = ref({
	title: null,
	content: null,
});

const goListPage = () => {
	router.push({
		name: 'PostList',
	});
};

const toStringByFormatting = (source, delimiter = '-') => {
	const year = source.getFullYear();
	const month = leftPad(source.getMonth() + 1);
	const day = leftPad(source.getDate());

	return [year, month, day].join(delimiter);
};

function leftPad(value) {
	if (value >= 10) {
		return value;
	}

	return `0${value}`;
}

const save = async () => {
	try {
		await createPost({
			...form.value,
			createdAt: toStringByFormatting(new Date()),
		});
		goListPage();
	} catch (error) {
		console.error(error);
	}
};
</script>

<style lang="scss" scoped></style>
