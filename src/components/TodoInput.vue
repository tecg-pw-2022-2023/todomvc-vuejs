<template>
  <input class="new-todo"
         autofocus
         autocomplete="off"
         placeholder="What needs to be done?"
         v-model="newTodo"
         @keyup.enter="addTodo">
</template>

<script>
let id = 1
export default {
  name: 'TodoInput',
  emits: ['newTodoAdded'],
  data() {
    return {
      newTodo: '',
    }
  },
  methods: {
    addTodo() {
      if(this.newTodo.trim()){
        let todo = {id: id++, title: this.newTodo, completed: false};
        this.$emit('newTodoAdded', todo)
        this.newTodo = ''
      }
    }
  }
};
</script>