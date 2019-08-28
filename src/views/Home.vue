<template>
  <div class="home">
      <Header></Header>
      <AddTodo v-on:add-todo="addTodo"/>
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Todos from '@/components/Todos';
import Header from '@/components/layout/Header';
import AddTodo from '@/components/AddTodo';
import axios from 'axios';
export default {
  name: 'Home',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [
      ]
    }
  },
  methods: {
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res=>this.todos = this.todos.filter(item=>item.id !== id))
      this.todos = this.todos.filter(item=>item.id !== id);
    },
    addTodo(newTodo){
      // data destructuring example
      const {title, completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data] );
      // array join interesting example
      this.todos = [...this.todos, newTodo];
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res=>{
      this.todos = res.data
    })
    .catch(err=>console.log(err));
    
  }
}
</script>
