<template>
  <div>
    <header class="site-header jumbotron">
      <div class="container">
        <div class="row">
          <div class="col-xs-12">
            <h1>请发表对Vue的评论</h1>
          </div>
        </div>
      </div>
    </header>
    <div class="container">
      <Add :addComment="addComment"/>
      <List :comments="comments" :deleteComment="deleteComment"/>
    </div>
  </div>
</template>

<script>
  import Add from './components/Add'
  import List from './components/List'
  export default {
    name: 'App',
    data(){   //数据在哪个组件，更新数据的行为就应该在哪个组件
      return{
        comments:[
          {
            name:'Bob',
            content:'Vue 怎么样'
          },
          {
            name:'mary',
            content:'Vue 简单'
          },
          {
            name:'Tom',
            content:'Vue 还可以'
          }
        ]
      }
    },
    methods:{
      //添加评论
      addComment(comment){
        this.comments.unshift(comment);
      },

      //删除评论
      deleteComment(index){
        this.comments.splice(index,1);
      }
    },
    components: {
      Add,
      List}
  }
</script>

<style scoped>

</style>
