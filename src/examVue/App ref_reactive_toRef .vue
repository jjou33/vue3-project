<template>
  <div>
    <h2>toRefs 미사용</h2>
    <p>{{ author }}</p>
    <p>{{ year }}</p>
    <h2>toRefs 사용</h2>
    <p>{{ author1 }}</p>
    <p>{{ year1 }}</p>
    <p>{{ name1 }}</p>
  </div>
</template>

<script>
import { reactive, ref, toRef, toRefs } from 'vue'

export default {
  setup() {
    // ref -> Object
    const count = ref(0)
    const state = reactive({
      count
    })
    count.value++
    count.value++
    console.log(count.value)
    // ref 일 경우  value 를 통해 값을 가져오지만,
    // reactive (반응형)에 연결을 하게 되면 없이 출력가능
    console.log('state : ', state.count)

    // ref -> Array

    const message = ref('hello')
    const arr = reactive([message])
    // 배열의 경우 반응형으로 연결을 해도 value 가 붙음
    console.log('arr[0]', arr[0].value)

    // reactive 구조분해 할당

    const book = reactive({
      author: 'Vue Team',
      year: '2020',
      name: 'hippo'
    })
    // 구조분해 할당을 하였을 경우 author, year 의 경우 반응성을 잃어버린다.
    // 즉, 단순 string 으로 변환된다.
    const { author, year } = book

    // 이를 해결하기 위해 toRefs 를 사용
    const book1 = reactive({
      author1: 'Vue Team',
      year1: '2020',
      name1: 'hippo'
    })
    // 여러개 받을 시
    const { author1, year1 } = toRefs(book1)
    // 한개만 받을 시
    const name1 = toRef(book1, 'name1')
    return {
      author,
      year,
      book,
      author1,
      year1,
      name1
    }
  }
}
</script>

<style lang="scss" scoped></style>
