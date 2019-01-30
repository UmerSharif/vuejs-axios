<template>
  <div>
      <input type="text" v-model="addtodo"/> 
    <button @click="addValue">Add</button>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data(){
      return{
          addtodo: ''
      }
  },
  methods: {
      addValue(){
          this.$emit('add-value', this.addtodo)
          this.addtodo = ''
      }
  }
};
</script>

<style>
</style>
