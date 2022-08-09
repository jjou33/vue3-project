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
      </div>
    </main>
  </div>
</template>

<script>
import { reactive } from 'vue'
import TheCard from './TheCard.vue'
import CreateButton from './PostCreate.vue'
export default {
  components: {
    TheCard,
    CreateButton
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
    const createPost = newTitle => {
      console.log('createPost', newTitle)
    }
    return { post, posts, createPost }
  }
}
</script>

<style lang="scss" scoped></style>
