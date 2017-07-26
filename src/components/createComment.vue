<template>
  <div id="createComment">
    <div class="well well-lg" :class="{hidden: hideComment}">
      <div class="row">
        <form class="col-md-4 row">
          <div class="input-group">
            <span class="input-group-addon form-label" id="basic-addon1">Username:</span>
            <input type="text" class="form-control" aria-describedby="basic-addon1" v-model="newComment.username">
          </div>
          <div class="input-group">
            <span class="input-group-addon form-label" id="basic-addon1">Description:</span>
            <textarea rows="4" class="form-control" aria-describedby="basic-addon1" v-model="newComment.body"/>
          </div>
            <button type="button" class="btn btn-info col-xs-12" @click="addComment">Submit</button>
        </form>
        <comment :commentData='newComment'>
        </comment>
      </div>
    </div>
  </div>
</template>
<script>
import comment from './comment.vue'

export default {
  name: "createComment",
  components: {
    comment
  },
  props: ['hideComment', 'onAddComment'],
  data () {
    return {
      newComment:{
        username: '',
        body: '',
        score: 0
      }
    }
  },
  methods: {
    addComment() {
      this.onAddComment({
        username: this.newComment.username,
        body: this.newComment.body,
        score: 0
      })
      this.newComment.username = ''
      this.newComment.body = ''
    }
  }
}
</script>
<style scoped>
.hidden{
  display: none;
}
</style>
