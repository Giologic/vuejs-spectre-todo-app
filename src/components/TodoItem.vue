<template>
  <div class="todo-item-custom">
    <div>
        <input class="mr-2 leading-tight" type="checkbox" v-on:change="markComplete" :checked="todo.completed"/>
        <span class="todo-title" v-bind:class="{'is-complete':todo.completed}">{{ todo.title }}</span>
    </div>
    <button @click="$emit('del-todo', todo.id)" class="svg-button rounded-full">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path class="heroicon-ui" d="M4.93 19.07A10 10 0 1 1 19.07 4.93 10 10 0 0 1 4.93 19.07zm1.41-1.41A8 8 0 1 0 17.66 6.34 8 8 0 0 0 6.34 17.66zM13.41 12l1.42 1.41a1 1 0 1 1-1.42 1.42L12 13.4l-1.41 1.42a1 1 0 1 1-1.42-1.42L10.6 12l-1.42-1.41a1 1 0 1 1 1.42-1.42L12 10.6l1.41-1.42a1 1 0 1 1 1.42 1.42L13.4 12z"/></svg>
    </button>
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
  .svg-button{
    fill: #e53e3e;
  }
  .svg-button:hover {
    fill: #9b2c2c;
  }
</style>