<template>
  <button class="clear-completed"
          @click="clearCompleted">
    Clear completed
  </button>
</template>

<script>
export default {
  name: 'clear-completed',
  methods: {
    clearCompleted() {
      this.$emit('clearCompleted')
    }
  }
};
</script>