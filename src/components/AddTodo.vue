<template>
  <div>
    <input type="text" v-model="addtodo">
    <button @click="addValue">Submit</button>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  // todosLenth prop is sent from app so that new id is calculated based on the array length
  props: ["todosLength"],
  data() {
    return {
      addtodo: ""
    };
  },
  methods: {
    addValue() {
      const newTodo = {
        id: this.todosLength + 1,
        Title: this.addtodo,
        isCompleted: false
      };
      this.$emit("add-value", newTodo);
      this.addtodo = "";
    }
  }
};
</script>

<style>
</style>
