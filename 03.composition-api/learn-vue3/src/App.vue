<template>
  <div>{{ counter }}</div>
  <button @click="addCounter">Increment</button>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const counter = ref(0)
    const addCounter = () => {
      counter.value++
    }

    return {
      counter,
      addCounter,
    }
  },
}
</script>

<style lang="scss" scoped></style>
