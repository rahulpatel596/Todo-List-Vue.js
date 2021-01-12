<template>
<div id="app">

  <AddTodo v-on:add-todo="addTodo"/>
<Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
</div>
</template>

<script>
import axios from 'axios';
import Todos from '../components/Todos.vue';
import AddTodo from '../components/AddTodo.vue';

export default {
  name: 'Home',
  components: {

    Todos,
    AddTodo
  },
  data() {
    return{
      todos:[
        
      ]
    }
  },
  methods: {
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => {console.log(res.data);
      this.todos = this.todos.filter(todo => todo.id !== id);}
      )
      .catch(err => console.error(err))

      this.todos = this.todos.filter(
        todo => todo.id !== id
      );
    },
    addTodo(newTodo){
      const {title, completed} = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {title,completed}).
      then( res => this.todos = [...this.todos, res.data])
      .catch(err => console.error(err))
      this.todos = [...this.todos, newTodo]
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
    .then(res => this.todos = res.data)
    .catch(err => console.error(err));
  }
}
</script>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
}

body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;

}
.btn{
  background:#666;
  color:#fff;
}
</style>
