<template>
<span class="todo-count">
      <strong>{{count+' item'+(count>1?'s':'')}}</strong> left
    </span>
</template>

<script>

export default {
  name: 'todo-count',
  props: ['count'],
};
</script>