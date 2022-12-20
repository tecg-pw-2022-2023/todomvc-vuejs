<template>
  <ul class="todo-list">
    <li :class="{completed: todo.completed, editing: todo == editedTodo}"
        v-for="todo in todoList">
      <div class="view">
        <input class="toggle"
               type="checkbox"
               v-model="todo.completed">
        <label @dblclick="editTodo(todo)">{{ todo.title }}</label>
        <button class="destroy"
                @click="removeTodo(todo)"></button>
      </div>
      <input class="edit"
             type="text"
             v-model="todo.title"
             v-todo-focus="todo == editedTodo"
             @blur="doneEdit(todo)"
             @keyup.enter="doneEdit(todo)"
             @keyup.esc="cancelEdit(todo)">
    </li>
  </ul>
</template>

<script>
const todoFocus = {
  updated: (el, binding) => binding.value ? el.focus() : el.blur()
}

export default {
  data() {
    return {
      editedTodo: null,
      titleBeforeEdit: '',
    }
  },
  directives: {
    todoFocus
  },
  emit: ['removeTodo'],
  props: {
    // Note that this a computed property, a filtered Array coming from parent
    // So you can't change its structure by removing an item for instance.
    // To remove or add an item, you have to ask the parent to do it
    // on the original Array
    todoList: Array,
  },
  methods: {
    editTodo(todo) {
      this.titleBeforeEdit = todo.title
      this.editedTodo = todo
    },
    doneEdit(todo) {
      if (!this.editedTodo) {
        return
      }
      this.editedTodo = null
      todo.title = todo.title.trim()
      if (!todo.title) {
        this.removeTodo(todo)
      }
      this.titleBeforeEdit = ''
    },
    cancelEdit(todo) {
      console.log('test')
      this.editedTodo = null
      todo.title = this.titleBeforeEdit
      this.titleBeforeEdit = ''
    },
    removeTodo(todo) {
      this.$emit('removeTodo', todo)
    }
  },
  name: 'todo-list'
}
</script>