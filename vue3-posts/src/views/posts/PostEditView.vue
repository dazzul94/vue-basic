<template>
	<div>
		<h2>게시글 수정</h2>
		<hr class="my-4" />
		<PostForm
			v-model:title="form.title"
			v-model:content="form.content"
			@submit.prevent="edit"
		>
			<template #actions>
				<button
					type="button"
					class="btn btn-outline-danger"
					@click="goDetailPage"
				>
					취소
				</button>
				<button class="btn btn-primary">수정</button>
			</template>
		</PostForm>
		<AppAlert :items="alerts" />
	</div>
</template>

<script setup>
import { getPostById, updatePost } from '@/api/posts';
import { markRaw, ref } from 'vue';
import { useRoute, useRouter } from 'vue-router';
import PostForm from './PostForm.vue';
import AppAlert from '@/components/AppAlert.vue';
const route = useRoute();
const router = useRouter();
const id = route.params.id;

const form = ref({
	title: null,
	content: null,
	createdAt: null,
});

const fetchForm = async () => {
	try {
		const { data } = await getPostById(id);
		setForm(data);
	} catch (error) {
		console.error(error);
	}
};

const setForm = ({ title, content, createdAt }) => {
	form.value.title = title;
	form.value.content = content;
	form.value.createdAt = createdAt;
};

fetchForm();

const edit = async () => {
	try {
		const data = {
			...form,
		};
		await updatePost(id, {
			...form.value,
		});
		vAlert('수정이 완료되었습니다.', 'success');
		// goDetailPage();
	} catch (error) {
		console.error(error);
		vAlert(error.message);
	}
};

const goDetailPage = () => {
	router.push({
		name: 'PostDetail',
		params: {
			id,
		},
	});
};

const alerts = ref([]);

const vAlert = (message, type) => {
	alerts.value.push({ message, type });

	setTimeout(() => {
		alerts.value.shift();
	}, 2000);
};
</script>

<style lang="scss" scoped></style>
