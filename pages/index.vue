<template>
  <div class="page-body index">
    <section class="recent-posts">
      <h1 class="title">RECENT POSTS</h1>
      <div class="posts-wrap">
        <Card
          v-for="(post, i) in posts"
          :id="post.sys.id"
          :key="i"
          :title="post.fields.title"
          :date="post.sys.updatedAt"
          class="post"
        />
      </div>
      <div class="buttom view-all">
        <a href="/postlist">
          <b-button @click="clickMe">VIEW ALL</b-button>
        </a>
      </div>
    </section>
    <section class="note-posts">
      <h1 class="title">NOTE POSTS</h1>
      <div class="tile is-2">
        <card class="post" />
      </div>
      <div class="buttom external">
        <a href="https://note.mu/mii_yo">
          <!-- TODO icon -->
          <b-button icon-right="note">VISIT</b-button>
        </a>
      </div>
    </section>
  </div>
</template>

<script>
import Card from '~/components/Card.vue'
import { createClient } from '~/plugins/contentful.js'

const client = createClient()
export default {
  transition: 'slide-left',
  components: {
    Card
  },
  asyncData({ env, params }) {
    return client.getEntries(env.CTF_BLOG_POST_TYPE_ID).then(entries => {
      return {
        posts: entries.items
      }
    })
    // .catch(console.error)
  }
}
</script>

<style lang="scss" scoped>
.page-body {
  section {
    margin-bottom: 90px;
  }
  .posts-wrap {
    display: flex;
    justify-content: flex-start;
  }
  .post + .post {
    margin-left: 20px;
  }
  .button {
    margin: 30px auto;
  }
}
</style>
