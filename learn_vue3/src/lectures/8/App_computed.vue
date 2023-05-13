<template>
	<div>
		<h2>{{ teacher.name }}</h2>
		<h3>강의가 있습니까?</h3>
		<!-- <p>{{ teacher.lectures.length > 0 ? '있음' : '없음' }}</p> -->
		<p>{{ hasLecture }}</p>
		<p>{{ existLecture() }}</p>
		<button @click="counter++">Counter: {{ counter }}</button>
		<h2>이름</h2>
		<p>{{ fullName }}</p>
	</div>
</template>

<script>
import { computed } from 'vue';
import { reactive, ref } from 'vue';

export default {
	setup() {
		const teacher = reactive({
			name: '김다솔',
			lectures: ['HTML/CSS', 'Javascript', 'Vue3'],
		});

		const hasLecture = computed(() =>
			teacher.lectures.length > 0 ? '0' : 'X',
		);
		const existLecture = () => (teacher.lectures.length > 0 ? '0' : 'X');

		const counter = ref(0);
		const firstName = ref('김');
		const lastName = ref('길동');

		const fullName = computed({
			get() {
				return firstName.value + ' ' + lastName.value;
			},
			set(value) {
				console.log('value: ' + value);
				const [first, last] = value.split(' ');
				console.log('first: ' + first);
				console.log('last: ' + last);
			},
		});
		console.log('출력:' + fullName.value);
		fullName.value = '김다솔';
		return {
			teacher,
			hasLecture,
			existLecture,
			counter,
		};
	},
};
</script>

<style lang="scss" scoped></style>
