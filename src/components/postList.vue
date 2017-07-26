<template>
  <div class="" id="postList">
    <form class="form-inline">
      <div class="form-group">
        <input type="search" class="form-control" id="search" placeholder="Enter search term" v-model='searchTerm'>
      </div>
    </form>
    <div v-for="singlePost in filteredPosts">
      <post :postData="singlePost"></post>
    </div>
  </div>
</template>
<script>
import post from './post'

export default {
  name: "postList",
  props: ['posts'],
  components: {
    post
  },
  data () {
    return {
      searchTerm: ''
    }
  },
  computed: {
    filteredPosts() {
      return this.posts.filter(post => {
         return post.title.toLowerCase().indexOf(this.searchTerm.toLowerCase()) > -1
      })
    },
    orderedPosts(){
      return this.posts.sort()
    }
  }
}
</script>
<style scoped>
</style>
