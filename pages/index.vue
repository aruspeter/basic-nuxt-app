<template>
  <Hello :data="posts" />
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData() {
    let data
    await fetch('https://jsonplaceholder.typicode.com/posts')
      .then((resp) => resp.json())
      .then((json) => {
        data = json
      })
    return {
      posts: { data },
    }
  },
}
</script>
