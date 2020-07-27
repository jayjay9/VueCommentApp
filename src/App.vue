<template>
  <div id="app">
    <Comment />
  </div>
</template>

<script>
import Comment from './components/Comment.vue'

export default {
  name: 'App',
  components: {
    Comment
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0 auto;
  max-width: 35%;
}
</style>
