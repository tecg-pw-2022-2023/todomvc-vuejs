<template>
  <input id="toggle-all" class="toggle-all" type="checkbox" @change="toggleAll">
  <label for="toggle-all">Mark all as complete</label>
</template>
<script>

export default {
  props: {
    todoList : Array,
  },
  methods:{
    toggleAll(){
      for (const todo of this.todoList) {
        todo.done  = !todo.done
      }
    }
  },
  name: 'toggle-all'
};
</script>
