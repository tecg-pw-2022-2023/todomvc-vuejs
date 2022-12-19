<template>
  <div>
  <input class="new-todo" autofocus autocomplete="off" placeholder="What needs to be done?" v-model="inputTodo" @keyup.enter="addTodo">
    <section class="main" v-show="todos.length">
      <input id="toggle-all" class="toggle-all" type="checkbox"  @change="allDone()">
      <label for="toggle-all">Mark all as complete</label>
      <ul class="todo-list">
        <li class="todo" v-for="todo in todos" :key="todo.id">
          {{ todo.text }} - {{todo.done}}
<!--          <div class="view">-->
<!--            <input class="toggle" type="checkbox" v-model="todo.completed">-->
<!--            <label @dblclick="editTodo(todo)">{{todo.title}}</label>-->
<!--            <button class="destroy" @click="removeTodo(todo)"></button>-->
<!--          </div>-->
<!--          <input class="edit" type="text" v-model="todo.title" v-todo-focus="todo == editedTodo" @blur="doneEdit(todo)" @keyup.enter="doneEdit(todo)" @keyup.esc="cancelEdit(todo)">-->
        </li>
      </ul>
    </section>
  </div>
</template>
<script>

let id = 1;
export default {
  name: 'InputTodo',

  data () {
    return {
      inputTodo: '',
      todos: [],
    }
  },
  methods: {
    addTodo () {
      this.todos.push({ id: id++, text: this.inputTodo, done: false })
      this.inputTodo = ''

    },
    filteredTodos(){
      let todo = this.todos.filter((todo)=>id === todo.id)[0];
    },
    allDone(){
      for (const todo of todos) {
        todo.done = !todo.done
      }
    }
  },
  computed: {
    todosDone(){
      return this.todos.filter((todo)=>todo.done)
    },
    todosUndone(){
      return this.todos.filter((todo)=>todo.done === false)
    },
},
}
</script>

<style scoped>

</style>