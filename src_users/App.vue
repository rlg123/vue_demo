<template>
  <div class="container">
    <Search/>
    <UsersMain/>
  </div>
</template>

<script>
  import Search from './components/Search'
  import Main from './components/Main'
  export default {
    data () {
      return {

      }
    },

    methods: {

    },

    // 声明接收标签属性
    props: {

    },

    //映射组件
    components: {
      Search,
      UsersMain:Main
    }
  }
</script>

<style>

</style>
