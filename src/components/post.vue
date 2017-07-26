<template>
  <div id="post" class="panel panel-default">
    <br />
    <div class="panel-heading row">
        <div class="scoreCounter col-xs-12 col-sm-4">
          <a @click="postData.score++"><span class="glyphicon glyphicon-arrow-up" aria-hidden="true"></span></a>
          <span>{{ postData.score }}</span>
          <a @click="postData.score > 0 ? postData.score-- : postData.score"><span class="glyphicon glyphicon-arrow-down" aria-hidden="true"></span></a>
        </div>
        <div class="col-xs-12 col-sm-4">
          <h3 class="panel-title">{{postData.title}} <small>By {{postData.username}} at {{postData.date}}</small></h3>
        </div>
      </div>
      <div class="panel-body">
        <div class="row">
          <div class="col-xs-4">
            <img v-bind:src="postData.img_url" :alt="postData.title" class="post-img img-responsive"/>
          </div>
          <div class="col-xs-8">
            <p>
              {{postData.description}}
            </p>
          </div>
        </div>
        <div><small>{{postComments}}</small></div>
        <button type='button' class='btn btn-lg btn-default' @click="hideComments = !hideComments">{{hideComments == true ? "Comments" : "Hide Comments"}}</button>
        <div class="row comments" :class="{hidden: hideComments}">
          <commentList :comments="postData.comments" :onAddComment="onAddComment"></commentList>
        </div>
      </div>
    </div>
</template>
<script>
import commentList from './commentList.vue'

export default {
  name: "post",
  props: ['postData'],
  components: {
    commentList
  },
  data () {
    return {
      hideComments: true
    }
  },
  methods: {
    onAddComment(comment){
      this.postData.comments.push(comment)
    }
  },
  computed: {
    postComments: function (){
      let comments = this.postData.comments.length;
      switch (true) {
        case comments == 1:
          return "1 Comment"
          break;
        default:
          return `${comments} Comments`
      }
    }
  }
}
</script>
<style scoped>
  .post-img{
    max-width: 200px;
    max-height: 200px;
    float: left;
  }
  .hidden{
    display: none;
  }
</style>
