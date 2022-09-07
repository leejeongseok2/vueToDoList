<template>
    <div id ="inputBox">
      <input id = "todo-input-box" type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" />
      <button id = "todo-insert-btn" type="button" v-on:click="addTodo" required>입력</button>
    </div>
    <template>

</template>

  </template>
  <script>
  export default {
    data: function() {
      return {
        newTodoItem: ""
      }
    },
    methods: {
      addTodo: function() {
        if (this.newTodoItem !== '') 
        {
        var obj = {completed: false, item: this.newTodoItem};
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        this.clearInput();
        }
      },
      clearInput: function() {
        this.newTodoItem=""; 
        window.location.reload();
      }
    }
  }
  </script>
  <style scoped>
  input:focus {
    outline: none;
  }
  .inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
  }
  .inputBox input {
    border-style: none;
    font-size: 0.9rem;
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
#todo-input-box {
    width: 40rem;
    height: 3rem;
    font-size: 2rem;
    background-color: rgb(255, 239, 209);
    border: 4px outset rgb(245, 227, 195);
    align-items: center;
}
  </style>