<script>
import TodoList from "./components/TodoList.vue";
import TodoForm from "./components/TodoForm.vue";

export default {
  components: {
    TodoList,
    TodoForm
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    submitHandler(todoObj) {
      this.todos = [...this.todos, todoObj];
    },
    removeHandler(id) {
      if (id) {
        this.todos = this.todos.filter((item) => item.id !== id);
      }
    },
    handleDone(id) {
      if (id) {
        this.todos = this.todos.map((todo) => {
          if (todo.id === id) {
            todo.done = !todo.done;
          }
          return todo;
        });
      }
    },
    removeDoneHandler() {
      this.todos = this.todos.filter((todo) => !todo.done);
    },
  },
};
</script>

<template>
  <TodoForm @create="submitHandler" :removeDoneHandler="removeDoneHandler"/>
  <section>
    <TodoList :todos="todos" :handleDone="handleDone" :removeHandler="removeHandler"/>
  </section>
</template>

<style scoped>

</style>
