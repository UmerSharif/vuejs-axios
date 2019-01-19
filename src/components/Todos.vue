<template>
  <div class="todos"><h1>Todo</h1>
<div v-for="todo in todos" :key="todo.id">
      
      <h1>
            {{todo.Title}}
      </h1>
      
      </div>  
  </div>
</template>

<script>
export default {
  name: "Todos",
  props: ["todos"]
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
