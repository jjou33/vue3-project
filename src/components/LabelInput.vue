<template>
  <label>
    <input
      :value="username"
      type="text"
      @input="event => (username = event.target.value)"
    />
  </label>
</template>

<script>
export default {
  props: ['modelValue'],
  emits: ['update:modelValue'],
  setup() {
    return {}
  }
}
</script>

<style lang="scss" scoped></style>
