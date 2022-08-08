<template>
  <div>
    <p>{{ original.count }}</p>
    <p>{{ copy_original.count }}</p>
  </div>
</template>

<script>
import { reactive, readonly } from 'vue'
export default {
  setup() {
    const original = reactive({
      count: 0
    })
    original.count++

    // read
    const copy_original = readonly(original)
    // 변경 가능
    original.count++
    // readonly 의 경우 변경불가
    copy_original.count++
    return { original, copy_original }
  }
}
</script>

<style lang="scss" scoped></style>
