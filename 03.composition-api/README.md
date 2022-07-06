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