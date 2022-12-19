<template>
  <ul class="todo-list">
    <li class="todo" v-for="todo in todoList">
      <div class="view">
        <template v-if="todo.done">
          <input class="toggle" type="checkbox" checked>
          <label>{{ todo.text }}</label>
        </template>
        <template v-else>
          <input class="toggle" type="checkbox">
          <label>{{ todo.text }}</label>
        </template>
        <button class="destroy"></button>
      </div>
      <input class="edit" type="text">

    </li>
  </ul>
</template>
<script>
export default {
  props: {
    todoList: Array,
  },
  methods:{
    toggle(todo){
      todo.done = !todo.done
    }
  },
  name: 'todo-list'
}
</script>