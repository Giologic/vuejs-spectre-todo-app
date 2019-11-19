<template>
  <div id="app" class="custom-container">
    <div class="header-section">
      <h2>Todo List</h2>
      <button class="btn btn-primary" @click="openModal">Add Todo</button>
    </div>
    <div class="loading loading-lg" v-if="loading"></div>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" v-else-if="!loading"/>
    <AddTodoModal v-bind:active="modalActive" v-on:close-modal="closeModal" v-on:add-todo="addTodo"></AddTodoModal>
  </div>
</template>

<script>
import Todos from './components/Todos.vue';
import axios from 'axios';
import AddTodoModal from './components/AddTodoModal.vue';

export default {
  name: 'app',
  components: {
    Todos,
    AddTodoModal
  },
  data() {
    return {
      todos: [],
      loading: true,
      errored: false,
      modalActive: false,
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter( todo => 
        todo.id !== id 
      )
    },
    openModal() {
      this.modalActive = true;
    },
    closeModal() {
      this.modalActive = false;
    },
    addTodo(title) {
      this.modalActive = false;
      let newTodo = {
        userId: 1,
        id: this.todos.length + 1,
        title,
        completed: false
      }
      this.todos = [...this.todos, newTodo]
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/todos')
    .then(response => {
      this.todos = response.data.slice(0,5)
    })
    .catch(error => {
      console.log(error)
      this.errored = true
    })
    .finally(() => this.loading = false)
  }
}
</script>

<style>
  .custom-container{
    margin: 20px 250px;
  }
  .header-section {
    display: flex;
    justify-content: space-between;
  }
</style>
