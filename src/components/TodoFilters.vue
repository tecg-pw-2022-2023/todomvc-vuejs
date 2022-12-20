<template>
  <ul class="filters">
    <li><a href="#/all"
           :class="{selected: filter == 'all'}"
           @click="this.filter='all'">All</a></li>
    <li><a href="#/active"
           :class="{selected:filter == 'active'}"
           @click="this.filter='active'">Active</a></li>
    <li><a href="#/completed"
           :class="{selected: filter == 'completed'}"
           @click="this.filter='completed'">Completed</a></li>
  </ul>
</template>
<script>
export default {
  name: 'todo-filters',
  data() {
    return {
      filter: 'all'
    }
  },
  emits: [
    'setFilter'
  ],
  watch: {
    filter(newFilter, oldFilter) {
      this.$emit('setFilter', newFilter)
    }
  }
};
</script>