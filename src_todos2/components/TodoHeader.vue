<template>
  <div class="todo-header">
    <input type="text" placeholder="请输入你的任务名称，按回车键确认"
           v-model="title" @keyup.enter="addItem"/>
  </div>
</template>

<script>
  export default {
    name: 'TodoHeader',
    data(){
      return{
        title:''
      }
    },
    props:{
    },
    methods:{
      addItem(){
        const title =this.title.trim()
        //1.检查输入的合法性
        if (!title){
          alert('任务名称不能为空')
          return
        }
        //2.根据输入封装对象
        const todo={
          title,
          complete:false
        }
        //3.将对象添加到数组中
        // this.addTodo(todo);
        //触发自定义事件：addTodo
        this.$emit('addTodo',todo)
        //4.清除输入框
        this.title=''
      }
    }
  }
</script>

<style scoped>
  /*header*/
  .todo-header input {
    width: 560px;
    height: 28px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 4px 7px;
  }

  .todo-header input:focus {
    outline: none;
    border-color: rgba(82, 168, 236, 0.8);
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
  }
</style>
