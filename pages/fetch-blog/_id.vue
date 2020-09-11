<template>
  <div v-if="post">
    <h1>{{ post.title }}</h1>
    <div>{{ post.body }}</div>
    <nuxt-link to="/fetch-blog">back to list</nuxt-link>
  </div>
</template>
<script>
export default {
  data () {
    return {
      post: null
    }
  },
  async fetch () {
    this.post = await this.$axios
      .$get(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
  }
}
</script>