<script>
export default {
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
    <ul v-for="todo in todos" key="todo.id" class="list-item">
      <li
        @click="handleDone(todo.id)"
        id="todoItem"
        v-bind:class="{ 'done-item': todo.done }"
      >
        {{ todo.todo }}
      </li>
      <button @click="removeHandler(todo.id)" class="remove-btn">Remove</button>
    </ul>
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
