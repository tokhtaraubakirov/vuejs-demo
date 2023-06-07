<template>
  <section class="form-container">
    <input type="text" v-model="inputValue" />
    <button @click="submitHandler" class="sumbit-btn">Submit</button>
    <button @click="removeDoneHandler" class="delete-all-btn">
      Remove All Done
    </button>
  </section>
</template>

<script>
export default {
  props: {
    removeDoneHandler: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
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
        this.$emit("create", todoObj);
        this.inputValue = "";
      }
    },
  },
};
</script>

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
.delete-all-btn {
  background-color: plum;
  color: white;
  padding: 0.5rem 1rem;
  border: 0;
  border-radius: 0.3rem;
}
</style>
