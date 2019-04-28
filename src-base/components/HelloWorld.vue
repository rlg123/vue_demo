<template>
  <div>
    <p class="msg">{{msg}}</p>
  </div>
</template>

<script>
  export default {  //配置对象
    data () {  //组件里面必须写函数
      return {
        msg: 'Hello Vue'
      }
    }
  }
</script>

<style>
  .msg {
    color: red;
    font-size: 30px;
  }
</style>
