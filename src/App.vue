<template>
  <div id="app">
   <h1>Записная книжка</h1>
   <app-addtodo @add-todo="addTodo" ></app-addtodo>
   <hr>
   <app-todoList 
   v-if="todos.length"
   v-bind:todos="todos"
   v-on:remove-todo="removeTodo"
   ></app-todoList>
   <h3 v-else>Записей нет</h3>
  </div>
</template>

<script>
import TodoList from './TodoList'
import Addtodo from './Addtodo'
export default {
  name: 'app',
  data () {
    return {
      todos:[
        {id:1, title: 'Купить фисташки', complited: false},
        {id:2, title: 'Купить лайм', complited: false},
        {id:3, title: 'Купить виски', complited: false},
      ]
    }
  },
  components:{
    'app-todoList': TodoList,
    'app-addtodo': Addtodo
  },
  methods:{
    removeTodo(id){
      this.todos = this.todos.filter(t=>t.id !== id)
    },
    addTodo(todo){
      this.todos.push(todo)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
