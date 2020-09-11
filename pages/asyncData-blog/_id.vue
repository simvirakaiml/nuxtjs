<template>
  <div>
    <h1> {{ post.title }} </h1>
    <div> {{ post.body }} </div>
    <nuxt-link to="/asyncData-blog">back to list</nuxt-link>
  </div>
</template>
<script>
export default {
  asyncData: ({ $axios, params, error }) => $axios
      .$get(`https://jsonplaceholder.typicode.com/posts/${params.id}`)
      .then(post => ({ post }))
      .catch(err => error({ statusCode: 404, message: 'Post not found' }))
};
</script>