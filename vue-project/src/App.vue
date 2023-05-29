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

	<!-- example5 -->
	<div>
		<ul>
			<template v-for="language in languages" :key="language.id">
				<li>
					{{ language.message }}
				</li>
			</template>
		</ul>
	</div>

	<!-- example6 -->
	<div>
		<button @click="printEventInfo('Hello Vue3', $event)">이벤트출력</button>
	</div>

	<!-- example7 -->
	<div>
		<!-- lazy -->
		<input type="text" v-model.lazy="vmodel" />
		<!-- <input type="text" @input="vmodel" /> -->
		<div>{{ vmodel }}</div>

		<div>
			<label for="checkbox">{{ checkboxValue }}</label>
			<input type="checkbox" id="checkbox" v-model="checkboxValue" />
		</div>

		<div>
			<label>
				<input type="radio" name="type" value="0" v-model="radioValue" />
				O형
			</label>
			<label>
				<input type="radio" name="type" value="B" v-model="radioValue" />
				B형
			</label>
			<div>혈액형: {{ radioValue }}형</div>
		</div>
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

		// example6
		const printEventInfo = (message, event) => {
			console.log('messag: ', message)
			console.log('event.target: ', event.target)
			console.log('event.target.tagName: ', event.target.tagName)
		}

		// example7
		const vmodel = ref('null')
		const checkboxValue = ref(true)
		const radioValue = ref('O')

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
			printEventInfo,
			vmodel,
			checkboxValue,
			radioValue,
		}
	},
}
</script>

<style scoped>
.active {
	font-weight: 1000;
}
</style>
