<template>
    <div>
      <p>ID:{{$route.params.id}}</p>
      <ul>
        <li>id:{{messageDetail.id}}</li>
        <li>title:{{messageDetail.title}}</li>
        <li>content:{{messageDetail.content}}</li>
      </ul>
    </div>
</template>

<script>

  export default {
    data () {
      return {
        messageDetail:{}
      }
    },
    mounted(){
      setTimeout(()=>{
        const allMessageDetails=[
          {
            id:1,
            title:'message001',
            content:'message001 content...'
          },
          {
            id:3,
            title:'message003',
            content:'message003 content...'
          },
          {
            id:4,
            title:'message004',
            content:'message004 content...'
          }
        ]
        this.allMessageDetails=allMessageDetails
        const id=this.$route.params.id*1
        this.messageDetail=allMessageDetails.find(detail=> detail.id===id)
      },1000)
    },
    watch:{   //路由路径发送改变
      $route:function (value) {
        const id=value.params.id*1
        this.messageDetail=this.allMessageDetails.find(detail=> detail.id===id)
      }
    },
    methods: {

    },

    // 声明接收标签属性
    props: {

    },

    //映射组件
    components: {

    }
  }
</script>

<style>

</style>
