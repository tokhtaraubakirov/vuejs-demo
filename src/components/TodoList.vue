<template>
  <ul v-for="todo in todos" :key="todo.id" class="list-item">
    <li
      @click="handleDone(todo.id)"
      id="todoItem"
      v-bind:class="{ 'done-item': todo.done }"
    >
      {{ todo.todo }}
    </li>
    <button @click="removeHandler(todo.id)" class="remove-btn">Remove</button>
  </ul>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      required: true,
    },
    handleDone: {
      type: Function,
      required: true,
    },
    removeHandler: {
      type: Function,
      required: true,
    },
  },
};
</script>

<style scoped>
.list-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 10%;
  cursor: pointer;
}

.list-item li {
  color: black;
  font-size: 1.5rem;
}
.remove-btn {
  background-color: red;
  color: white;
  padding: 0.5rem 1rem;
  border: 0;
  border-radius: 0.3rem;
}

.done-item {
  text-decoration: line-through;
}
</style>
