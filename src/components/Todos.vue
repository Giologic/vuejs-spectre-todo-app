<template>
  <div>
    <div class="form-group" v-if="todos.length > 0">
      <div v-bind:key="todo.id" v-for="todo in todos">
        <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
      </div>
    </div>
    <Hero v-else></Hero>
    
  </div>
  
</template>

<script>
import TodoItem from './TodoItem.vue'
import Hero from './Hero.vue'

export default {
  name: "Todos",
  components: {
    TodoItem,
    Hero
  },
  props: ["todos"]
}
</script>

<style scoped>

</style>