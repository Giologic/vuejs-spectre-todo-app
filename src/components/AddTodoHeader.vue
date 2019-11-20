<template>
  <form v-on:submit.prevent="addToTodoList">
    <div class="flex items-center border-b border-b-2 border-blue-500 py-2">
      <input v-model="title" class="appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none" type="text" placeholder="Buy groceries" aria-label="Full name">
      <button type="submit" class="flex-shrink-0 bg-blue-500 hover:bg-blue-700 border-blue-500 hover:border-blue-700 text-sm border-4 text-white py-1 px-2 rounded">
        Add Todo
      </button>
    </div>
  </form>
</template>

<script>
export default {
  name: 'AddTodoHeader',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addToTodoList() {
      if (this.title.length === 0) {
        this.$emit('alert-empty')
      }
      else {
        this.$emit('add-todo', this.title)
        this.title = ''
      }
    }
  }
}
</script>

<style scoped>

</style>