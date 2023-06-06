<script>
export default {
  data() {
    return {
      todos: [],
      inputValue: "",
    };
  },
  methods: {
    submitHandler() {
      if (this.inputValue) {
        let todoObj = {
          id: new Date().valueOf(),
          todo: this.inputValue,
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
  },
};
</script>

<template>
  <section class="form-container">
    <input type="text" v-model="inputValue" />
    <button @click="submitHandler" class="sumbit-btn">Submit</button>
  </section>
  <section>
    <ul v-for="todo in todos" key="todo.id" class="list-item">
      <li>
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
