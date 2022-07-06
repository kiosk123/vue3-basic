# 뷰 시작하기
- `v-bind`와 `v-model`의 차이: `v-bind`는 **단방향** 바인딩 `v-model`은 **양방향** 바인딩!!!
- 싱글파일 컴포넌트로 개발하기 위해서는 빌드도구인 `vite`나 `Vue-CLI`가 필요하다
```bash
npm i vue
npm i vite # vite 설치
```
- vite.config.js 설정 [참고](https://github.com/vitejs/vite/tree/main/packages/plugin-vue)
```js
// vite.config.js
import vue from '@vitejs/plugin-vue'
export default {
  plugins: [vue()]
}
```