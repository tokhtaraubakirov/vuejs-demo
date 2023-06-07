<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    handleDone: {
      type: Function,
      required: true,
    },
  },
};
</script>

<template>
  <li
    @click="handleDone(todo.id)"
    id="todoItem"
    v-bind:class="{ 'done-item': todo.done }"
    class="todo-item"
  >
    {{ todo.todo }}
  </li>
</template>

<style scoped>
.done-item {
  text-decoration: line-through;
}
</style>
