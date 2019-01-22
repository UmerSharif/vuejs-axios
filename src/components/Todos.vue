<template>
  <div class="todos">
    <h1>Todo</h1>
    <div v-for="todo in todos" :key="todo.id">
      <TodoItem v-bind:todo="todo" v-on:del-todonode="sendToApp(todo.id)"/>
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"],
  methods: {
    sendToApp(Node_ID) {
      this.$emit("del-node", Node_ID);
      // console.log(this.todo.id)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
