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
  width: 22.6rem;
  cursor: pointer;
  padding: .5rem;
  background-color: #0A2647;
}

.list-item li {
  color: white;
  font-size: 1.3rem;
  list-style: none;
}
.remove-btn {
  background-color: red;
  color: white;
  padding: 0.5rem 1rem;
  border: 0;
  border-radius: 0.3rem;
}
</style>
