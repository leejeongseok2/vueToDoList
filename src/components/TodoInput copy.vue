<template>
    <div id="todoinput">
      <input id = "todo-input-box" type="text" v-model="content" @keyup.enter="addToDo" />
      <button id = "todo-insert-btn" type="button" @click="addToDo">등록</button>
    </div>
  </template>
  <script>
  export default {
    data() {
      return {
        content: ''
      }
    },
    methods: {
      addToDo() {
        this.$emit('add-to-do', this.content)
        this.content = ''
      }
    }
  }
  </script>
  
<style>
#todo-input-box {
    width: 40rem;
    height: 3rem;
    font-size: 2rem;
    background-color: rgb(255, 239, 209);
    border: 4px outset rgb(245, 227, 195);
    align-items: center;
}
#todo-insert-btn {
    width: 10rem;
    height: 3.7rem;
    font-size: 2rem;
    background-color: rgb(255, 239, 209);
    border: 4px outset rgb(245, 227, 195);
    cursor: pointer;
    align-items: right;
}
</style>