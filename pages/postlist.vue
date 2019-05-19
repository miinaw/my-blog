<template>
  <div class="content">
    <div class="tile is-2">
      <card
        v-for="(post, i) in posts"
        :id="post.sys.id"
        :key="i"
        :title="post.fields.title"
        :date="post.sys.updatedAt"
        class="post"
      />
    </div>
  </div>
</template>

<script>
import Card from '~/components/card.vue'
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
