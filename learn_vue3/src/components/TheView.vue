<template>
	<main>
		<div class="container py-4">
			<MyButton id="my-button" class="my-button" @click="sayHello"></MyButton>
			<LabelInput label="이름" data-id="id입니다"></LabelInput>
			<hr />
			<FancyButton>Click!<span style="color: red">@@@</span></FancyButton>
			<FancyButton>
				<template v-slot="{ fancyMessage }">{{
					fancyMessage
				}}</template></FancyButton
			>
			<hr />
			<AppCard>
				<!-- <template #[slotArgs]>제목입니다.</template> -->
				<!-- 암시적인 default slot 바디입니다.
				<template #footer>푸터입니다.</template> -->
				<template #header="{ headerMessage }"> {{ headerMessage }}</template>
				<template #default="{ childMessage, helloMessage }"
					>Default slot {{ message }} {{ childMessage }}
					{{ helloMessage }}</template
				>
				<template #footer="{ footerMessage }"> {{ footerMessage }}</template>
			</AppCard>
		</div>
	</main>
</template>

<script>
import LabelInput from './LabelInput.vue';
import MyButton from './MyButton.vue';
import FancyButton from './FancyButton.vue';
import AppCard from './AppCard.vue';
import { ref } from 'vue';

export default {
	components: {
		MyButton,
		LabelInput,
		FancyButton,
		AppCard,
	},
	setup() {
		const sayHello = () => {
			alert('안녕하세요');
		};
		const slotArgs = ref('header');
		const message = ref('안녕');
		return { sayHello, slotArgs, message };
	},
};
</script>

<style lang="scss" scoped></style>
