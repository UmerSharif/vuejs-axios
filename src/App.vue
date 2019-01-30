<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:del-node="DeleteNode"/>
    <add-todo v-on:add-value="addData" />
  </div>
</template>

<script>
import Header from "./components/layout/Header";
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo"

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          Title: "Read",
          isCompleted: false
        },
        {
          id: 2,
          Title: "Write",
          isCompleted: false
        },
        {
          id: 3,
          Title: "Speak",
          isCompleted: false
        }
      ]
    };
  },

  methods: {
    DeleteNode(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addData(todoVal){
      this.todos.push({id: this.todos.length + 1, Title: todoVal, isCompleted: false})
    }
  }
};
</script>

<style>
#app {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
