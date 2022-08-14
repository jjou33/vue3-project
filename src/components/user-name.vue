<template>
  <div>
    <LabelInput
      :model-value="firstname"
      label="성"
      @update:model-value="value => $emit('update:firstName', value)"
    ></LabelInput>
    <LabelInput
      :model-value="lastname"
      label="이름"
      @update:model-value="value => $emit('update:lastName', value)"
    ></LabelInput>
  </div>
</template>

<script>
import LabelInput from './LabelInput.vue'

export default {
  components: {
    LabelInput
  },
  props: ['firstName', 'lastName'],
  emits: ['update:firstName', 'update:lastName'],
  setup() {
    return {}
  }
}
</script>

<style lang="scss" scoped></style>
