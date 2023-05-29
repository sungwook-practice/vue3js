<template>
	<!-- example1 -->
	<div>
		<div>{{ counter }}</div>
		<div>{{ message }}</div>
	</div>

	<!-- example2 -->
	<div>
		<div>선생님 이름: {{ teacher.name }}</div>
		<p>{{ hasLecture }}</p>
	</div>
	<button @click="increment">counter 증가</button>

	<!-- example3 -->
	<div>
		<div :class="{ active: isActive }">active 테스트</div>
		<button @click="toggleActvie">active On/Off</button>
	</div>

	<!-- example4 -->
	<div>
		<h2 v-if="character === 'A'">A입니다</h2>
		<h2 v-else-if="character === 'B'">B입니다</h2>
		<h2 v-else-if="character === 'C'">C입니다</h2>

		<button v-on:click="character = 'A'">A로변경</button>
		<button v-on:click="character = 'B'">B로변경</button>
		<button v-on:click="character = 'C'">C로변경</button>
	</div>

	<!-- example4 -->
	<div>
		<ul>
			<template v-for="language in languages" :key="language.id">
				<li>
					{{ language.message }}
				</li>
			</template>
		</ul>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue'

export default {
	setup() {
		// example1
		const counter = ref(0)
		const message = ref('hello world')
		const increment = () => {
			counter.value++
		}

		// example2
		const teacher = reactive({
			name: 'John',
			lecture: ['HTML/css', 'Javascript', 'Vue3'],
		})
		const hasLecture = computed({
			get() {
				return teacher.lecture.length > 0 ? '강의 있음' : '값의 없음'
			},
		})

		// example3
		let isActive = ref(true)
		const toggleActvie = () => {
			isActive.value = !isActive.value
		}

		// example4
		const character = ref('C')

		// example5
		const languages = reactive([
			{ id: 1, message: 'java' },
			{ id: 2, message: 'html' },
			{ id: 3, message: 'css' },
		])

		return {
			counter,
			message,
			increment,
			teacher,
			hasLecture,
			isActive,
			toggleActvie,
			character,
			languages,
		}
	},
}
</script>

<style scoped>
.active {
	font-weight: 1000;
}
</style>
