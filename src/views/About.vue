<template>
    <div>
      <h2>About</h2>
      <p>{{msg}}</p>
      <input type="text">
    </div>
</template>

<script>
  export default {
    data () {
      return {

      }
    },

    methods: {

    },

    // 声明接收标签属性
    props: {
      msg:String
    },

    //映射组件
    components: {

    }
  }
</script>

<style>

</style>
