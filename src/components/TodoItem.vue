<template>
  <div class="todo-item-custom">
    <div>
        <input class="mr-2 leading-tight" type="checkbox" v-on:change="markComplete" :checked="todo.completed"/>
        <span class="todo-title" v-bind:class="{'is-complete':todo.completed}">{{ todo.title }}</span>
    </div>
    <button @click="$emit('del-todo', todo.id)" class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-3 rounded">Delete</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed
    }
  }
}
</script>

<style scoped>
  .is-complete {
    text-decoration: line-through;
  }
  .todo-item-custom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5px;
  }
  .todo-title{
    padding-left: 10px;
  }
  .custom-label input:checked + svg {
    display: block !important;
  }
</style>