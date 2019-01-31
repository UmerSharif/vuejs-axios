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
import axios from "axios"

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
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addData(todoVal) {
      this.todos.push(todoVal);
    }
  },

    created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
    .then(res => this.todos = res.data)
    .catch(err => console.log(err))
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
