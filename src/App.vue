<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:/>
  </div>
</template>

<script>
//import HelloWorld from "./components/HelloWorld";
import Todos from "./components/Todos";

export default {
  name: "App",
  components: {
    Todos
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
