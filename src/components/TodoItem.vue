<template>
  <div class="todo-item-custom">
    <div>
      <label class="form-checkbox">
        <input type="checkbox" v-on:change="markComplete" :checked="todo.completed"/>
        <i class="form-icon"></i> <span class="todo-title" v-bind:class="{'is-complete':todo.completed}">{{ todo.title }}</span>
      </label>
    </div>
    <button @click="$emit('del-todo', todo.id)" class="btn btn-error">Delete</button>
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
    padding: 5px;
  }
  .todo-title{
    padding-left: 10px;
  }
</style>