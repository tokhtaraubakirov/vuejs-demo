<script>
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    TodoList
  },
  data() {
    return {
      todos: [],
      inputValue: "",
      done: false,
    };
  },
  methods: {
    submitHandler() {
      if (this.inputValue) {
        let todoObj = {
          id: new Date().valueOf(),
          todo: this.inputValue,
          done: this.done,
        };
        this.todos.push(todoObj);
        this.inputValue = "";
      }
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
  <section class="form-container">
    <input type="text" v-model="inputValue" />
    <button @click="submitHandler" class="sumbit-btn">Submit</button>
    <button @click="removeDoneHandler" class="sumbit-btn">Remove All Done</button>
  </section>
  <section>
    <TodoList :todos="todos" :handleDone="handleDone" :removeHandler="removeHandler"/>
  </section>
</template>

<style scoped>
.form-container {
  display: flex;
  justify-content: space-between;
  width: 10%;
}
.sumbit-btn {
  background-color: green;
  color: black;
  padding: 0.5rem 1rem;
  border: 0;
  border-radius: 0.3rem;
}
</style>
