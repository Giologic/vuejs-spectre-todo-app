<template>
  <div id="app" class="mx-auto px-64">
    <div class="header-section">
      <h1 class="text-3xl font-bold text-gray-900">Todo List</h1>
      <AlertEmpty v-if="alertEmptyIsActive"></AlertEmpty>
      <AddTodoHeader v-on:add-todo="addTodo" v-on:alert-empty="alertEmpty"></AddTodoHeader>
    </div>
    <div class="loader" v-if="loading">Loading</div>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" v-else-if="!loading"/>
  </div>
</template>

<script>
import Todos from './components/Todos.vue';
// import axios from 'axios';
import AddTodoHeader from './components/AddTodoHeader.vue';
import AlertEmpty from './components/AlertEmpty.vue';
import uuidv4 from 'uuid/v4';

export default {
  name: 'app',
  components: {
    Todos,
    AddTodoHeader,
    AlertEmpty
  },
  data() {
    return {
      todos: [],
      // loading: true,
      errored: false,
      alertEmptyIsActive: false,
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter( todo => 
        todo.id !== id 
      )
    },
    addTodo(title) {
      this.alertEmptyIsActive = false
      let newTodo = {
        userId: 1,
        id: uuidv4(),
        title,
        completed: false
      }
      this.todos = [...this.todos, newTodo]
    },
    alertEmpty() {
      this.alertEmptyIsActive = true
    }
  },
  // mounted() {
  //   axios.get('https://jsonplaceholder.typicode.com/todos')
  //   .then(response => {
  //     this.todos = response.data.slice(0,5)
  //   })
  //   .catch(error => {
  //     console.log(error)
  //     this.errored = true
  //   })
  //   .finally(() => this.loading = false)
  // }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Open+Sans&display=swap');


  * {
    font-family: 'Open Sans', sans-serif;
  }
  .header-section {
    display: flex;
    flex-direction: column;
    padding: 30px 0px;
  }
  .loader,
  .loader:before,
  .loader:after {
    border-radius: 50%;
    width: 2.5em;
    height: 2.5em;
    -webkit-animation-fill-mode: both;
    animation-fill-mode: both;
    -webkit-animation: load7 1.8s infinite ease-in-out;
    animation: load7 1.8s infinite ease-in-out;
  }
  .loader {
    color: #4299e1;
    font-size: 10px;
    margin: 80px auto;
    position: relative;
    text-indent: -9999em;
    -webkit-transform: translateZ(0);
    -ms-transform: translateZ(0);
    transform: translateZ(0);
    -webkit-animation-delay: -0.16s;
    animation-delay: -0.16s;
  }
  .loader:before,
  .loader:after {
    content: '';
    position: absolute;
    top: 0;
  }
  .loader:before {
    left: -3.5em;
    -webkit-animation-delay: -0.32s;
    animation-delay: -0.32s;
  }
  .loader:after {
    left: 3.5em;
  }
  @-webkit-keyframes load7 {
    0%,
    80%,
    100% {
      box-shadow: 0 2.5em 0 -1.3em;
    }
    40% {
      box-shadow: 0 2.5em 0 0;
    }
  }
  @keyframes load7 {
    0%,
    80%,
    100% {
      box-shadow: 0 2.5em 0 -1.3em;
    }
    40% {
      box-shadow: 0 2.5em 0 0;
    }
  }
</style>
