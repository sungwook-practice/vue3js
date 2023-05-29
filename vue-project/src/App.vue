<template>
   <!-- example1 -->
  <p>
    <div>{{ counter }}</div>
    <div>{{ message }}</div>
  </p>

  <br/>

  <!-- example2 -->
  <p>
    <div>선생님 이름: {{ teacher.name }}</div>
    <p>{{ hasLecture }}</p>
  </p>
  <button @click="increment">counter 증가</button>

  <!-- example3 -->
  <br/>

  <p>
    <div :class="{ active: isActive}">active 테스트</div>
    <button @click="toggleActvie">active On/Off</button>
  </p>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
  setup () {
    // example1
    const counter = ref(0);
    const message = ref('hello world')
    const increment = () => {
      counter.value ++;
    }

    // example2
    const teacher = reactive({
      name: 'John',
      lecture: ['HTML/css', 'Javascript', 'Vue3']
    })
    const hasLecture = computed({
      get() {
        return teacher.lecture.length > 0 ? '강의 있음' : '값의 없음'
      }
    })

     // example3
    let isActive = ref(true);
    const toggleActvie = () => {
      isActive.value = !isActive.value
    }

    return {
      counter,
      message,
      increment,
      teacher,
      hasLecture,
      isActive,
      toggleActvie
    }
  }
}
</script>

<style scoped>
.active {
  font-weight: 1000;
}
</style>