<script>
import TodoItem from "./TodoItem.vue";

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
  components: {
    TodoItem,
  },
};
</script>

<template>
  <ul v-for="todo in todos" :key="todo.id" class="list-item">
    <TodoItem :todo="todo" :handleDone="handleDone" />
    <button @click="removeHandler(todo.id)" class="remove-btn">Remove</button>
  </ul>
</template>

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
</style>
