<template>
  <div>
    <main>
      <div class="container py-4">
        <CreateButton @create-post="createPost"></CreateButton>
        <hr class="my-4" />
        <div class="row g-3">
          <div v-for="post in posts" :key="post.id" class="col col-4">
            <TheCard
              :title="post.title"
              :contents="post.contents"
              :is-like="post.isLike"
              :type="post.type"
              @toggle-like="post.isLike = !post.isLike"
            ></TheCard>
          </div>
        </div>
        <hr class="my-4" />
        <!-- <LabelInput
          :model-value="userName"
          @update:model-value="value => (userName = value)"
        ></LabelInput> -->
        <LabelInput v-model="userName"></LabelInput>
        <UserName
          v-model:firstName="firstName"
          v-model:lastName="lastName"
        ></UserName>
      </div>
    </main>
  </div>
</template>

<script>
import { reactive, ref } from 'vue'
import TheCard from './TheCard.vue'
import CreateButton from './PostCreate.vue'
import LabelInput from './LabelInput.vue'
import UserName from './user-name.vue'

export default {
  components: {
    TheCard,
    CreateButton,
    LabelInput,
    UserName
  },
  setup() {
    const post = reactive({
      title: '제목2',
      contents: '내용2'
    })

    const posts = reactive([
      {
        id: 1,
        title: '제목1',
        contents: '내용2',
        isLike: true,
        type: 'temp'
      },
      {
        id: 2,
        title: '제목2',
        contents: '내용2',
        isLike: true,
        type: 'temp'
      },
      {
        id: 3,
        title: '제목3',
        contents: '내용2',
        isLike: false,
        type: 'temp'
      },
      {
        id: 4,
        title: '제목4',
        contents: '내용2',
        isLike: false,
        type: 'news'
      },
      {
        id: 5,
        title: '제목5',
        contents: '내용2',
        isLike: true,
        type: 'news'
      }
    ])
    const createPost = newPost => {
      console.log('createPost', newPost)
      posts.push(newPost)
    }
    const userName = ref('')
    return { post, posts, createPost, userName }
  }
}
</script>

<style lang="scss" scoped></style>
