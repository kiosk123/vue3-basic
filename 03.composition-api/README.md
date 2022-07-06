# 컴포지션 API
## 1. ref, isRef
- ref: 반응형 데이터를 생성
- isRef: 반응형 데이터 여부를 검사
```vue
<template>
  <div>
    <h2>반응형 메시지</h2>
    <p>{{ reactiveMessage }}</p>
    <button @click="addReactiveMessage">Add Message</button>
    <h2>일반 메시지</h2>
    <p>{{ normalMessage }}</p>
  </div>
</template>

<script>
import { ref, isRef } from 'vue'

export default {
  setup() {
    const reactiveMessage = ref('Hello Reactive Message')
    const addReactiveMessage = () => {
      reactiveMessage.value = reactiveMessage.value + '!'
    }
    console.log('isRef(reactiveMessage): ', isRef(reactiveMessage)) // 반응형 데이터 인지 검사

    const normalMessage = 'Hello'
    console.log('isRef(normalMessage): ', isRef(normalMessage)) // 반응형 데이터 인지 검사
    return {
      reactiveMessage,
      normalMessage,
      addReactiveMessage,
    }
  },
}
</script>

<style lang="scss" scoped></style>
```

## 라이프 사이클 훅
```js
import { onBeforeMount, onMounted } from 'vue'

export default {
  setup() {
    //...

    onBeforeMount(() => {
      console.log('onBeforeMount')
    })

    onMounted(() => {
      console.log('onMounted')
    })

    //...
  },
}
```

## 템플릿 문법
```vue
<template>
  <div v-once>{{ message }}</div> <!-- v-once 한번만 출력-->
  <button @click="add">add !</button>
  <p v-html="rawHtml"></p> <!-- v-html은 html엘리먼트 그대로 출력-->
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
```