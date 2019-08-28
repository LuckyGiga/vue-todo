<template>
  <div>
    <div v-for="todo in todos" v-bind:key="todo.id">
      <Todo 
        :todo="todo"  
        v-on:del-todo="$emit('del-todo', todo.id)" 
        v-on:complete-todo="$emit('complete-todo')"
      />
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