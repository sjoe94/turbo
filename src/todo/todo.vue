<template>
  <section class="real-app">
    <input type="text" class="add-input" autofocus="autofocus" placeholder="接下来要做什么？" @keyup.enter="addTodo"> 
    <item :todo="todo" v-for="todo in todos" :key="todo.id" @del="deleteTodo"/>>  
    <tabs :filter="filter" :todos="todos"></tabs>  
  </section>
</template>
<script>
import Item from './item.vue'
import Tabs from './tabs.vue'
export default {
  methods:{
    data(){
      return {
        todo:{
          id:0,
          content:'this is todo',
          completed:false
        },
        filter:'all'   
      }
    },
    components:{
      Item,Tabs
    },
    methods:{
      addTodo(e){
        this.todos.unshift({
          id:id++,
          content:e.target.value.trim(),
          completed:false
        })
        e.target.value=''
      },
      deleteTodo(id){
        this.todos.splice(this.todos.findIndex(todo=>todo.id==id),1)
      }
    },
    
  }
}
</script>
<style lang="stylus" scoped>
.real-app{
  width 37.5rem /* 600/16 */
  margin 0 auto 
  box-shadow 0 0 5px #666}
.add-input{
  position relative
  }
</style>


