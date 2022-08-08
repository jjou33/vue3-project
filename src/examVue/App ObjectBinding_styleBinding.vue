<template>
  <div>
    <div class="text" :class="{ active: isActive, 'text-danger': hasError }">
      텍스트 입니다.
    </div>

    <button @click="toggle">toggle</button>
    <button @click="checkError">CheckError</button>
    <div :class="classObject">클레스 오브젝트</div>
    <div :class="classObjectCompute">클레스 오브젝트 Compute</div>

    <div :style="styleObject">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias dolore
      vitae est hic dignissimos, repudiandae voluptate obcaecati quasi odit!
      Repellendus, tempore autem saepe ea illo iure similique atque. Corporis,
      ipsa!
    </div>
    <button @click="fontSize--">-</button>
    <button @click="fontSize++">+</button>
  </div>
</template>

<script>
import { computed, reactive, ref } from 'vue'

export default {
  setup() {
    const isActive = ref(true)
    const hasError = ref(false)
    const toggle = () => {
      isActive.value = !isActive.value
    }
    const checkError = () => {
      hasError.value = !hasError.value
    }
    const classObject = reactive({
      active: true,
      'text-danger': true
    })

    const classObjectCompute = computed(() => {
      return {
        active: false,
        'text-danger': true
      }
    })

    // styleObject
    const fontSize = ref(14)
    const styleObject = computed(() => {
      return {
        color: 'red',
        fontSize: fontSize.value + 'px'
      }
    })
    return {
      classObjectCompute,
      isActive,
      toggle,
      hasError,
      checkError,
      classObject,
      styleObject,
      fontSize
    }
  }
}
</script>

<style lang="css" scoped>
.active {
  font-weight: 900;
}

.text-danger {
  color: red;
}
</style>
