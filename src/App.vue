<script>
import TodoInput from '@/components/TodoInput.vue';
import ToggleAll from "@/components/ToggleAll.vue";
import TodoList from "@/components/TodoList.vue";
import TodoCount from "@/components/TodoCount.vue";
import TodoFilters from "@/components/TodoFilters.vue";
import ClearCompleted from "@/components/ClearCompleted.vue";
import toggleAll from "@/components/ToggleAll.vue";

export default {
  components: {
    ClearCompleted,
    TodoFilters,
    TodoCount,
    TodoList,
    ToggleAll,
    TodoInput,
  },
  data() {
    return {
      todoList: [],
      filter: 'all',
    }
  },
  methods: {
    toggleAll(value) {
      this.todoList.forEach(t => t.completed = value)
    },
    removeTodo(todo) {
      this.todoList.splice(this.todoList.indexOf(todo), 1)
    },
    clearCompleted() {
      let completedTodos = this.todoList.filter(todo => todo.completed)
      completedTodos.forEach(todo => this.removeTodo(todo))
    }

  },
  computed: {
    filteredTodos() {
      switch (this.filter) {
        case "completed":
          return this.todoList.filter(t => t.completed)
        case "active":
          return this.todoList.filter(t => !t.completed)
        case "all":
        default:
          return this.todoList
      }
    }
  }
}
</script>

<template>
  <header class="header">
    <h1>todos</h1>
    <todo-input @newTodoAdded="todo =>  this.todoList.push(todo)"/>
  </header>
  <section class="main">
    <toggle-all @toggleAll="toggleAll"/>
    <todo-list @removeTodo="removeTodo"
               :todoList="filteredTodos"/>
  </section>
  <footer class="footer"
          v-show="todoList.length">
    <todo-count :count="todoList.filter(t=>!t.completed).length"/>
    <todo-filters @setFilter="(filter) => this.filter = filter"/>
    <clear-completed @clearCompleted="clearCompleted"
                     v-show="todoList.filter(t=>t.completed).length"/>
  </footer>
</template>
