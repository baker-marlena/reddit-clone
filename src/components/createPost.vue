<template>
  <div id="createPost">
    <div class="well well-lg" :class="{hidden: hidePost}">
      <div class="row">
        <form class="col-md-4 row">
          <div class="form-group" v-bind:class="{ 'has-error': blur.title && isEmpty(newPost.title)}">
            <label class="form-label">* Title:</label>
            <input type="text" class="form-control form-control-warning" aria-describedby="basic-addon1" v-model="newPost.title" @blur="blur.title = true">
          </div>
          <div class="form-group" v-bind:class="{ 'has-error': blur.username && isEmpty(newPost.username) }">
            <label  class="form-label">* Username:</label>
            <input type="text" class="form-control" aria-describedby="basic-addon1" v-model="newPost.username" @blur="blur.username = true">
          </div>
          <div class="form-group" v-bind:class="{ 'has-error': blur.img_url && isEmpty(newPost.img_url) }">
            <label  class="form-label">* Image URL:</label>
            <input type="url" class="form-control" aria-describedby="basic-addon1" v-model="newPost.img_url" @blur="blur.img_url = true">
          </div>
          <div class="form-group" v-bind:class="{ 'has-error': blur.description && isEmpty(newPost.description) }">
            <label class="form-label">* Description:</label>
            <textarea rows="4" class="form-control" aria-describedby="basic-addon1" v-model="newPost.description" @blur="blur.description = true"/>
          </div>
            <button type="button" class="btn btn-info col-xs-12" @click="addPost">Submit</button>
        </form>
        <!-- <post :postData='newPost'>
        </post> -->
      </div>
      </div>
    </div>
</template>
<script>
import post from './post'

export default {
  name: "createPost",
  props: ['hidePost','onAddPost'],
  components: {
    post
  },
  data () {
    return {
      newPost: {
        title: '',
        username: '',
        img_url: '',
        description: ''
      },
      blur: {
        title: false,
        username: false,
        img_url: false,
        description: false
      }
    }
  },
  methods: {
    addPost () {
      if(this.isEmpty(this.newPost.title) || this.isEmpty(this.newPost.username) || this.isEmpty(this.newPost.img_url) || this.isEmpty(this.newPost.description)){
        alert('All fields are required.')
      }
      else{
        this.onAddPost({
          title: this.newPost.title,
          username: this.newPost.username,
          img_url: this.newPost.img_url,
          score: 0,
          date: new Date(),
          description: this.newPost.img_url,
          comments: []
        });
        this.newPost.title = '';
        this.newPost.username = '';
        this.newPost.img_url = '';
        this.newPost.description = '';
        this.blur.title = false;
        this.blur.username = false;
        this.blur.img_url = false;
        this.blur.description = false;
      }
    },
    isEmpty (value) {
      return value === ''
    }
  }
}
</script>
<style scoped>
  .hidden{
    display: none;
  }
</style>
