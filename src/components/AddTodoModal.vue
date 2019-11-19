<template>
  <div class="modal" v-bind:class="{'active': active}" id="modal-id">
    <a href="#close" class="modal-overlay" aria-label="Close"></a>
    <div class="modal-container">
      <div class="modal-header">
        <a href="#close" class="btn btn-clear float-right" aria-label="Close" @click="$emit('close-modal')"></a>
        <div class="modal-title h5">Add Todo</div>
      </div>
      <div class="modal-body">
        <div class="content">
          <div @keydown.enter="addToTodoList" class="form-group">
            <label class="form-label" for="input-example-3">Todo</label>
            <input v-model="title" class="form-input" type="text" placeholder="Buy groceries" />
            <br />
            <button @click="addToTodoList" class="btn btn-primary">Submit</button>
          </div>
        </div>
      </div>
      <div class="modal-footer">
        ...
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AddTodoModal',
  props: ["active"],
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addToTodoList() {
      if(this.title !== '' ) {
        this.$emit('add-todo', this.title)
        this.title=''
      }
    }
  }
}
</script>

<style scoped>

</style>