<template>
  <div class="home">
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Todos from '@/components/Todos';

export default {
  name: 'home',
  components: {
    Todos,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title : "First Todo",
          completed: false
        },
        {
          id: 2,
          title : "Second Todo",
          completed: true
        },
        {
          id: 3,
          title : "Third Todo",
          completed: false
        },
      ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(item=>item.id !== id);
    }
  },
}
</script>
