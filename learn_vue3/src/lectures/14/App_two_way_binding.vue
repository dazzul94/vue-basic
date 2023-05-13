<template>
	<div>
		<h2>Input Value</h2>
		<!-- <input type="text" v-model.lazy="inputValue" /> -->
		<!-- <input type="text" v-model.number="inputValue" /> -->
		<input type="text" v-model.trim="inputValue" />
		<div>{{ inputValue }}</div>
		<!-- <div>{{ typeof inputValue }}</div> -->
		<textarea v-model="textAreaValue"></textarea>
		<div>{{ textAreaValue }}</div>
		<h2>checkbox value</h2>
		<label for="checkbox">{{ checkboxValue }}</label>
		<input
			type="checkbox"
			id="checkbox"
			v-model="checkboxValue"
			true-value="YES"
			false-value="NO"
		/>
		<h2>radio value</h2>
		<label>
			<input type="radio" name="type" value="O" v-model="radioValue" />
			O형
		</label>
		<label>
			<input type="radio" name="type" value="A" v-model="radioValue" />
			A형
		</label>
		<div>
			{{ radioValue }}
		</div>
		<h2>select value</h2>
		<select v-model="selectValue">
			<option value="html">HTML</option>
			<option value="java">JAVA</option>
			<option value="css">CSS</option>
		</select>
		<div>{{ selectValue }}</div>
		<h2>checkbox values</h2>
		<label>
			<input type="checkbox" value="html" v-model="checkboxValues" />
			HTML
		</label>
		<label>
			<input type="checkbox" value="java" v-model="checkboxValues" />
			JAVA
		</label>
		<label>
			<input type="checkbox" value="css" v-model="checkboxValues" />
			CSS
		</label>
		<div>{{ checkboxValues }}</div>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const inputValue = ref('');
		const textAreaValue = ref('');
		const checkboxValue = ref('YES');
		const radioValue = ref('O');
		const selectValue = ref('html');
		const checkboxValues = ref([]);

		return {
			inputValue,
			textAreaValue,
			checkboxValue,
			radioValue,
			selectValue,
			checkboxValues,
		};
	},
};
</script>

<style lang="scss" scoped></style>
