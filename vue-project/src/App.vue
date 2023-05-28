<template>
  <p>
    <div>{{ counter }}</div>
    <div>{{ message }}</div>
  </p>
  <button @click="increment">counter 증가</button>
</template>

<script>
import { ref } from 'vue';

export default {
  setup () {
    const counter = ref(0);
    const message = ref('hello world')
    const increment = () => {
      counter.value ++;
    }
    return {
      counter,
      message,
      increment
    }
  }
}
</script>

<style lang="scss" scoped>

</style>