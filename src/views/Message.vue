<template>
    <div>
      <ul>
        <li v-for="(message,index) in messages" :key="message.id">
          <router-link :to="`/home/message/detail/${message.id}`">{{message.title}}</router-link>
          <button @click="pushShow(message.id)">push查看</button>
          <button @click="replaceShow(message.id)">replace查看</button>
        </li>
      </ul>
      <button @click="$router.back()">回退</button>
      <hr>
      <router-view></router-view>
    </div>
</template>

<script>
  export default {
    data () {
      return {
        messages:[]
      }
    },
    mounted(){
      //模拟ajax请求从后台获取数据
      // setTimeout() 方法用于在指定的毫秒数后调用函数或计算表达式
      setTimeout(()=>{
         const messages=[
           {
             id:1,
             title:'message001',
           },
           {
             id:3,
             title:'message003',
           },
           {
             id:4,
             title:'message004',
           }
         ]
        this.messages=messages
      },1000)
    },
    methods: {
      pushShow(id){
        this.$router.push(`/home/message/detail/${id}`)
      },
      replaceShow(id){
        this.$router.replace(`/home/message/detail/${id}`)
      }
    },

    //映射组件
    components: {

    }
  }
</script>

<style>

</style>
