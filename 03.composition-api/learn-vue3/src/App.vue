<template>
  <div v-once>{{ message }}</div>
  <button @click="add">add !</button>
  <p v-html="rawHtml"></p>
  <h2>속성 바인딩</h2>
  <div :title="dynamicTitle">마우스를 올려보세요</div>

  <!-- 객체를 이용한 속성 바인딩-->
  <input v-bind="attrs" />

  <!-- 템플릿 안에 자바스크립트 함수도 사용가능 -->
  <div>{{ [...message].reverse().join('') }}</div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const message = ref('안녕하세요')
    const rawHtml = ref('<strong>안녕하세요</strong>')
    const dynamicTitle = ref('안녕하세요!!!!')
    const attrs = ref({
      typs: 'password',
      value: '12345678',
      disabled: false,
    })

    const add = () => {
      message.value = message.value + '!'
    }

    return {
      message,
      add,
      rawHtml,
      dynamicTitle,
      attrs,
    }
  },
}
</script>

<style lang="scss" scoped></style>
