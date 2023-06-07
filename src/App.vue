<script>
import TodoList from "./components/TodoList.vue";
import TodoForm from "./components/TodoForm.vue";

export default {
  components: {
    TodoList,
    TodoForm,
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
  <main class="todo-container">
    <TodoForm @create="submitHandler" :removeDoneHandler="removeDoneHandler" />
    <section>
      <TodoList
        v-if="todos.length > 0"
        :todos="todos"
        :handleDone="handleDone"
        :removeHandler="removeHandler"
      />
      <div v-else class="empty-list-container">
        <h2 class="empty-list">Empty list</h2>
        <img src="/doge.png" alt="doge image" class="doge-img">
      </div>
    </section>
  </main>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap");

body {
  background-color: #03001c;
  font-family: "Roboto", sans-serif;
}

.todo-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20rem;
  height: 100vh;
}

.empty-list-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 2rem;
}

.empty-list {
  color: white;
  text-transform: uppercase;
}

.doge-img {
  width: 300px;
  height: auto;
}
</style>
