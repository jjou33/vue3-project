<template>
  <div>
    <h2>{{ teacher.name }}</h2>
    <h2>강의가 있나여?</h2>
    <p>computed 미사용 : {{ teacher.lecture.length > 0 ? '있음' : '없음' }}</p>
    <p>computed 사용 : {{ hasLecture }}</p>
    <p>computed 사용 : {{ existedLecture() }}</p>
    <h2>블로그 명</h2>
    <p>{{ fullName }}</p>
  </div>
</template>

<script>
import { reactive, computed, ref } from 'vue'

export default {
  setup() {
    const teacher = reactive({
      name: 'hippo',
      lecture: ['HTML/CSS', 'Javascript', 'Vue3']
    })

    // computed 의 경우 여러번 호출되었을떄
    // 한번 계산되었을때 결과를 cache 에 저장해두고
    // 다음 호출 때 뿌려준다.
    // 따라서. method 보다 computed 로 사용하는게 효율적이다.
    const hasLecture = computed(() => {
      console.log('computed')
      return teacher.lecture.length > 0 ? '있음' : '없음'
    })

    // 반면 method 의 경우 cache 가 일어나지 않고 계속 실행된다.
    const existedLecture = () => {
      console.log('method')
      return teacher.lecture.length > 0 ? '있음' : '없음'
    }
    // 즉, 브라우저가 재랜더링을 진행하더라도 다시 계산하지 않고 cache 된
    // 결과를 사용하므로 성능상 유리하다.

    const firstName = ref('Hippo')
    const lastName = ref('Dev')
    // const fullName = computed(() => {
    //   return firstName.value + ' ' + lastName.value
    // })
    // 아래와 같이 computed 된 속성을 변경할 경우 readonly 로 인해 불가능하다.
    // fullName.value = 'Dev Hippo'

    // 따라서, get, set 함수를 통해 변경해야한다.
    const fullName = computed({
      get() {
        return firstName.value + ' ' + lastName.value
      },
      set(value) {
        ;[firstName.value, lastName.value] = value.split(' ')
      }
    })

    // get, set 함수를 정의하면 가능하다.
    fullName.value = 'Dev Hippo'

    return {
      teacher,
      hasLecture,
      existedLecture,
      fullName
    }
  }
}
</script>

<style lang="scss" scoped></style>
