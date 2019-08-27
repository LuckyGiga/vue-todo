<template>
  <div>
    <h1>Todos</h1>
    <div v-for="todo in todos" v-bind:key="todo.id">
      <Todo :todo="todo"  v-on:del-todo="$emit('del-todo', todo.id)"/>
    </div>
  </div>
</template>

<script>
import Todo from '@/components/Todo'
export default {
  name: "Todos",
  props: ["todos"],
  components:{
    Todo,
  }
}
</script>


<style scoped>

</style>