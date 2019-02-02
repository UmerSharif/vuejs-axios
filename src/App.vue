<template>
  <div id="app">
    <Header/>
    <Todos v-bind:todos="todos" v-on:del-node="DeleteNode"/>
    <add-todo v-bind:todosLength="todosLength" v-on:add-value="addData"/>
  </div>
</template>

<script>
import Header from "./components/layout/Header";
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import axios from "axios";

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },

  methods: {
    DeleteNode(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => (this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => console.log(err));
    },
    addData(todoVal) {
      const { title, isCompleted } = todoVal;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          isCompleted
        })
        .then(res => (this.todos = [...this.todos, res.data]))
        .catch(err => console.log(err));
      // this.todos.push(todoVal);
    }
  },

  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err));
  },
  computed: {
    todosLength() {
      return this.todos.length;
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
