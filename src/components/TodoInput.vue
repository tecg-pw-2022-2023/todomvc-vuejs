<template>
  <input class="new-todo" autofocus autocomplete="off" placeholder="What needs to be done?" v-model="inputTodo" @keyup.enter="addTodo">
</template>
<script>
let id = 1
export default {
  name: 'TodoInput',
  emits: ['inputTodo'],
  data () {
    return {
      inputTodo: '',
    }
  },

  methods: {

    addTodo () {
      console.log(this.inputTodo)
      let todo = { id: id++, text: this.inputTodo, done: false };
      this.$emit('inputTodo', todo)
      this.inputTodo = ''
    }
  },
};
</script>
<style>
</style>