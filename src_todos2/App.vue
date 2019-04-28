<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <!--<TodoHeader @addTodo="addTodo"/>  &lt;!&ndash;给TodoHeader标签对象绑定addTodo事件监听&ndash;&gt;-->
      <TodoHeader ref="header"/>
      <TodoList :todos="todos" />
      <todo-footer>
        <input type="checkbox" v-model="isAllCheck" slot="checkAll"/>
        <span slot="count">已完成{{completeSize}}/ 全部{{todos.length}}</span>
        <button class="btn btn-danger" v-show="completeSize>0" @click="deleteCompleteTodos" slot="delete">清除已完成任务</button>
      </todo-footer>
    </div>
  </div>
</template>
<!--
绑定事件监听  -----订阅消息
触发事件      -----发布消息
-->
<script>
  import PubSub from 'pubsub-js'
  import TodoHeader from './components/TodoHeader'
  import TodoList from './components/TodoList'
  import TodoFooter from './components/TodoFooter'
  import storageUtil from './util/storageUtil'
  export default {
    data(){
      return{
        // 从localStorage读取todos
        todos:storageUtil.readTodos()
      }
    },
    computed:{
      completeSize(){
        return this.todos.reduce((preTotal,todo)=>preTotal+(todo.complete?1:0),0 )
      },
      isAllCheck:{
        get(){
          return this.completeSize===this.todos.length && this.completeSize>0
        },
        set(value){   //value是当前checkbox的最新值
          this.selectAllTodos(value)
        }
      }
    },
    mounted(){  //执行异步代码
      //给 <TodoHeader />绑定addTodo事件监听
      this.$refs.header.$on('addTodo',this.addTodo);

      //订阅消息
      PubSub.subscribe('deleteTodo', (msg,index)=> {
        this.deleteTodo(index);
      })
    },
    methods:{
      addTodo(todo){
        this.todos.unshift(todo);
      },
      deleteTodo(index){
        this.todos.splice(index,1)
      },
      //删除所有选中的todo
      deleteCompleteTodos(){
        this.todos=this.todos.filter(todo=>!todo.complete)
      },
      //全选/全不选
      selectAllTodos(check){
        this.todos.forEach(todo=>todo.complete=check)
      }
    },
    watch:{  //深度监视
      todos:{
        deep:true,  //深度监视
        /*handler:function (value) {
          //将todos最新值的json数据，保存到localStorage
          // window.localStorage.setItem('todos_key',JSON.stringify(value))
          storageUtil.saveTodos(value)
        }*/
        handle: storageUtil.saveTodos
      }
    },
    components:{
      TodoHeader,
      TodoList,
      TodoFooter
    }
  }
</script>

<style >
  /*app*/
  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>
