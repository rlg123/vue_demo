<template>
  <div>
    <h2>Home</h2>
    <div>
      <ul class="nav nav-tabs">
        <li>
          <router-link to="/home/news">News</router-link>
        </li>
        <li>
          <router-link to="/home/message">Message</router-link>
        </li>
      </ul>

        <router-view></router-view>

    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {}
    },

    methods: {},

    // 声明接收标签属性
    props: {},

    //映射组件
    components: {}
  }
</script>

<style>

</style>
