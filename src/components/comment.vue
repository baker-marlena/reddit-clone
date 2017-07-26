<template>
  <div id="comment">
    <div class="panel panel-default">
      <div class="panel-body">
        <div class="row">
          <div class="scoreCounter col-sm-4">
            <a @click="commentData.score++"><span class="glyphicon glyphicon-arrow-up" aria-hidden="true"></span></a>
            <span>{{ commentData.score }}</span>
            <a @click="commentData.score--"><span class="glyphicon glyphicon-arrow-down" aria-hidden="true"></span></a>
          </div>
          <div class="col-xs-8">
            <p>{{commentData.body}}</p>
            <small class="col-xs-8">By {{commentData.username}}</small>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "comment",
  props: ['commentData'],
  data: () => ({

  })
}
</script>
<style scoped>
</style>
