<script>
import TodoInput from '@/components/TodoInput.vue';
import ToggleAll from "@/components/ToggleAll.vue";
import TodoList from "@/components/TodoList.vue";
import TodoCount from "@/components/TodoCount.vue";
import TodoFilters from "@/components/TodoFilters.vue";
import ClearCompleted from "@/components/ClearCompleted.vue";
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
    return{
    todoList : []
    }
  }
};
</script>
<template>
  <header class="header">
    <h1>todos</h1>
    <todo-input @inputTodo="(todo) =>  this.todoList.push(todo)"/>
  </header>
  <section class="main">
    <toggle-all :todoList="todoList"></toggle-all >
    <todo-list :todoList="todoList"/>
  </section>
  <footer class="footer">
    <todo-count/>
    <todo-filters/>
    <clear-completed/>
  </footer>
</template>
