<template>
  <div class="home">
      <AddTodo v-on:add-todo="addTodo"/>
      <Todos 
        v-bind:todos="todos" 
        v-on:del-todo="deleteTodo"
        v-on:complete-todo="completeTodo"
      />
  </div>
</template>

<script>
// @ is an alias to /src
import Todos from '@/components/Todos';
import AddTodo from '@/components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
      ],


    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(item=>item.id !== id);
      localStorage.setItem('vue-todo',JSON.stringify(this.todos));
    },
    addTodo(newTodo){
      console.log(newTodo);
      this.todos = [...this.todos, newTodo];
      localStorage.setItem('vue-todo',JSON.stringify(this.todos));
    },
    completeTodo() {
      localStorage.setItem('vue-todo',JSON.stringify(this.todos));
    },
  },
  created(){
    const importTodos= JSON.parse(localStorage.getItem('vue-todo'));
    this.todos = importTodos?importTodos:[];
  }
}
</script>
