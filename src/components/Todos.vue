<template>
  <div class="todos">
    <h1>Todo</h1>
    <div v-for="todo in todos" :key="todo.id">
     <TodoItem v-bind:todo="todo" />
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem'
export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"]
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
