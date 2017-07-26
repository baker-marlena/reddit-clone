<template>
  <div id="commentList">
    <div>
      <button class='btn btn-default' @click="toggleShow">{{hidden == true ? "Comment" : "Hide Comment Form"}}</button>
    </div>
    <createComment :hideComment="hidden" :onAddComment="onAddComment"></createComment>
    <div v-for="comment in comments">
      <comment :commentData="comment"></comment>
    </div>
  </div>
</template>
<script>
import comment from './comment.vue'
import createComment from './createComment.vue'
import posts from '../lib/posts'

export default {
  name: "commentList",
  props: ['comments','onAddComment'],
  components: {
    comment,
    createComment
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
    }
}
}
</script>
<style scoped>
</style>
