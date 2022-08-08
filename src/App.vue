<template>
  <div v-memo="[subscriber]">
    <p>subscribers: {{ subscriber }}</p>
    <p>views: {{ views }}</p>
    <p>likes: {{ likes }}</p>
  </div>
  <button @click="subscriber++">sub++</button>
  <button @click="views++">views++</button>
  <button @click="likes++">likes++</button>
  <div>
    <p>subscribers: {{ subscriber }}</p>
    <p>views: {{ views }}</p>
    <p>likes: {{ likes }}</p>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const subscriber = ref(4000)
    const views = ref(400)
    const likes = ref(20)
    // v-memo 의 경우 배열안에 명시한 값이 변경할때만 재랜더링함
    // 나머지는 v-once 와 비슷
    return { subscriber, views, likes }
  }
}
</script>

<style lang="scss" scoped></style>
