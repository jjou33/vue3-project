<template>
  <div>
    <h2>데이터 변경</h2>
    <p>{{ message }}</p>
    <button @click="modifyMessage">Click</button>
    <h2>반응형</h2>
    <button @click="increment">Click {{ state.count }}</button>
    <button @click="increment">Deep Click {{ state.deep.count }}</button>
  </div>
</template>

<script>
import { reactive, ref } from 'vue'

export default {
  setup() {
    const message = ref('안녕하세요')

    const modifyMessage = () => {
      message.value += '!'
    }

    const state = reactive({
      count: 0,
      deep: {
        count: 0
      }
    })
    const increment = () => {
      state.count++
      state.deep.count++
    }
    return { message, modifyMessage, state, increment }
  }
}
</script>

<style lang="scss" scoped></style>
