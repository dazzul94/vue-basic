<template>
	<div>
		<h2>게시글 목록</h2>
		<hr class="my-4" />
		<PostFilter v-model:title="params.title_like" v-model:limit="params._limit">
		</PostFilter>
		<hr class="my-4" />
		<AppGrid :items="posts">
			<template v-slot="{ item }">
				<PostItem
					:title="item.title"
					:content="item.content"
					:created-at="item.createdAt"
					@click="goPage(item.id)"
					@modal="openModal(item)"
				></PostItem>
			</template>
		</AppGrid>
		<AppPagination
			:current-page="params._page"
			:page-count="pageCount"
			@page="page => (params._page = page)"
		/>
		<Teleport to="#modal">
			<PostModal
				v-model="show"
				:title="modalTitle"
				:content="modalContent"
				:created-at="modalCreatedAt"
			>
				<template #default>
					<div class="row">
						<div class="col-3">제목</div>
						<div class="col-9">{{ modalTitle }}</div>
						<div class="col-3">내용</div>
						<div class="col-9">{{ modalContent }}</div>
						<div class="col-3">등록일</div>
						<div class="col-9">{{ modalCreatedAt }}</div>
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
			</PostModal>
		</Teleport>

		<template v-if="posts && posts.length">
			<hr class="my-4" />
			<AppCard>
				<PostDetailView :id="posts[0].id"></PostDetailView>
			</AppCard>
		</template>
	</div>
</template>

<script setup>
import PostItem from '@/components/posts/PostItem.vue';
import PostDetailView from '@/views/posts/PostDetailView.vue';
import AppCard from '@/components/AppCard.vue';
import { ref, watchEffect } from 'vue';
import { getPosts } from '@/api/posts.js';
import { useRouter } from 'vue-router';
import { computed } from 'vue';
import AppPagination from '@/components/AppPagination.vue';
import AppGrid from '@/components/AppGrid.vue';
import PostFilter from '@/components/posts/PostFilter.vue';
import AppModal from '@/components/AppModal.vue';
import PostModal from '@/components/posts/PostModal.vue';

const router = useRouter();
const posts = ref([]);
const params = ref({
	_sort: 'createdAt',
	_order: 'desc',
	_page: 1,
	_limit: 3,
	title_like: '',
});
const totalCount = ref(0);
const pageCount = computed(() =>
	Math.ceil(totalCount.value / params.value._limit),
);

const fetchPosts = async () => {
	try {
		const { data, headers } = await getPosts({ ...params.value });
		posts.value = data;
		totalCount.value = headers['x-total-count'];
	} catch (error) {
		console.error(error);
	}
};
fetchPosts();

// 콜백함수 내에서 반응형 상태가 변경되어 다시 실행함
watchEffect(fetchPosts);

const goPage = id => {
	router.push({
		name: 'PostDetail',
		params: { id },
	});
};

// modal
const show = ref(false);
const modalTitle = ref('');
const modalContent = ref('');
const modalCreatedAt = ref('');

const openModal = ({ title, content, createdAt }) => {
	show.value = true;
	modalTitle.value = title;
	modalContent.value = content;
	modalCreatedAt.value = createdAt;
};
const closeModal = () => {
	show.value = false;
};
</script>

<style lang="scss" scoped></style>
