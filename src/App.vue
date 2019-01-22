<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:del-node="DeleteNode"/>
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
  },

  methods:{
    DeleteNode(id){
    this.todos = this.todos.filter(todo => todo.id !== id)
    
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
