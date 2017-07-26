<template>
  <div id="app">
    <navigation></navigation>
    <createPost :hidePost="hidden" :onAddPost="onAddPost"></createPost>
    <div>
      <button class="btn btn-lg btn-default" @click="toggleShow">{{hidden == true ? "Make a New Post" : "Hide New Post Form"}}</button>
    </div>
    <div class="btn-group" role="group" aria-label="...">
      <button @click="sortByDate" type="button" class="btn btn-default">Date</button>
      <button @click="sortByScore" type="button" class="btn btn-default">Score</button>
      <button @click="sortByTitle" type="button" class="btn btn-default">Title</button>
    </div>
    <postList :posts="posts"></postList>
  </div>
</template>

<script>
import navigation from './components/navigation.vue'
import createPost from './components/createPost.vue'
import postList from './components/postList.vue'
import posts from './lib/posts'

export default {
  name: 'app',
  components: {
    navigation,createPost,postList
  },
  data () {
    return {
      hidden: true,
      posts
    }
  },
  methods: {
    toggleShow() {
      this.hidden = !this.hidden;
    },
    onAddPost(post){
      this.posts.push(post)
    },
    sendSearch(term){
      searchTerm = term
    },
    sortByScore() {
      posts.sort(function (a, b) {
        return a.score.localeCompare(b.score);
      })
    },
    sortByDate() {
      posts.sort(function (a, b) {
        return a.date.localeCompare(b.date);
      })
    },
    sortByTitle() {
      posts.sort(function (a, b) {
        return a.title.localeCompare(b.title);
      })
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
