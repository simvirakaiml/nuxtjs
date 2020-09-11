<template>
  <div>
    <h1> Blog posts </h1>
    <div v-if="posts && posts.length">
      <div
        v-for="post in posts"
        :key="post.id">
        <nuxt-link :to="`/fetch-blog/${post.id}`">{{ post.title }}</nuxt-link>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      posts: []
    }
  },
  async fetch() {
    this.posts = await this.$axios.$get(`https://jsonplaceholder.typicode.com/posts`)
  }
};
</script>