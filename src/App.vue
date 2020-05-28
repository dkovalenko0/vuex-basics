<template>
  <div id="app">
    <PostForm></PostForm>
    <h1>{{ postsCount }}</h1>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h1 class="title">{{ post.title }}</h1>
      <p class="body">{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
import PostForm from "./components/PostForm";

export default {
  name: "App",
  computed: mapGetters(["validPosts", "postsCount"]),
  methods: mapActions(["fetchPosts"]),
  components: {
    PostForm
  },
  async mounted() {
    this.fetchPosts();
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
