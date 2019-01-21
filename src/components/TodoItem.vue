<template>
  <div class="todo-item" :class="{'is-complete':todo.isCompleted}">
    <input type="checkbox" @change="ToggleComplete">
    {{todo.id}} :{{todo.Title}}
    <button @click="sendToParent" class="del">x</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],

  methods: {
    ToggleComplete() {
      this.todo.isCompleted = !this.todo.isCompleted;
    },

    sendToParent() {
      this.$emit("del-todonode", this.todo.id);
      console.log(this.todo.id);
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
.is-complete {
  text-decoration: line-through;
}
.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
  outline: none;
}
</style>
