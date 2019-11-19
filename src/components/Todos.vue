<template>
  <div>
    <div class="form-group" v-if="todos.length > 0">
      <div v-bind:key="todo.id" v-for="todo in todos">
        <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
      </div>
    </div>
    <Jumbotron v-else></Jumbotron>
    
  </div>
  
</template>

<script>
import TodoItem from './TodoItem.vue'
import Jumbotron from './Jumbotron.vue'

export default {
  name: "Todos",
  components: {
    TodoItem,
    Jumbotron
  },
  props: ["todos"]
}
</script>

<style scoped>

</style>