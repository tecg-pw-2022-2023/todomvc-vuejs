<template>
  <input id="toggle-all"
         class="toggle-all"
         type="checkbox"
         v-model="allDone">
  <label for="toggle-all">Mark all as complete</label>
</template>

<script>
export default {
  data() {
    return {
      allDone: false,
    }
  },
  watch: {
    allDone(newValue) {
      this.$emit('toggleAll', newValue)
    },
  }
}
</script>
