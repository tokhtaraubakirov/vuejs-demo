<template>
  <section class="form-container">
    <input type="text" v-model.trim="inputValue" class="input" />
    <button @click="submitHandler" class="submit-btn">Submit</button>
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
  width: 19.85%;
}
.input {
  font-size: 1rem;
}
.submit-btn {
  background-color: #00337C;
  color: white;
  padding: .5rem 1rem;
  border: 0;
  border-radius: .3rem;
}
.submit-btn:hover {
  background-color: #003b8d;
}
.delete-all-btn {
  background-color: #3A1078;
  color: white;
  padding: .5rem .7rem;
  border: 0;
  border-radius: .3rem;
}
.delete-all-btn:hover {
  background-color: #471394;
}
</style>
