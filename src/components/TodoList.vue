<template>
    <div>
      <ul>
        
        <li v-for="(todoItem, index) in todoItems" v-bind:key="todoItem" id = "container">
          <button type="button" id="checkbox" v-on:click="checkItem(todoItem, index)" >V</button>
          {{ todoItem }}
          <button id = "todo-remove-btn" type="button" v-on:click="removeTodo(todoItem, index)">X</button>
        </li>
      </ul>
    </div>
</template>

<script>
  export default {
  data: function() {
    return {
      todoItems: []
    }
  },
  methods: {
    removeTodo: function(todoItem, index) {
        localStorage.removeItem(todoItem);
        this.todoItems.splice(index, 1); 
    },
    checkItem: function(todoItem, index) {
        this.todoItems[index].completed = !this.todoItems[index].completed;
        console.log(this.todoItems);
        localStorage.removeItem(todoItem.item);
        localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    }
  },
  created: function() {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i ++) {
        if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          this.todoItems.push(localStorage.key(i));
        }
      }
    }
  }
}
    </script>
    
    <style scoped>
    ul {
      list-style-type: none;
      padding-left: 0;
      margin-top: 0;
      text-align: center;
    }
    li {
      display: flex;
      min-height: 50px;
      height: 50px;
      line-height: 50px;
      margin: 0.5rem 0;
      padding: 0 0.9rem;
      background: white;
      border-radius: 5px;
      text-align: left;
    }
    .checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}

#container {
    width: 48.7rem;
    height: 3rem;
    font-size: 2rem;
    background-color: rgb(255, 239, 209);
    border: 4px outset rgb(245, 227, 195);
    margin: auto;
    display: inline-block;
    
}
#todo-remove-btn {
    opacity: 1;
    width: 3rem;
    height: 3rem;
    font-size: 1.5rem;
    border : 3px outset lightyellow;
    background-color: lightgoldenrodyellow;
    cursor: pointer;
    float: right;

    
}
#checkbox {
    width: 2.8rem;
    height: 2.8rem;
    margin-right:1rem;
    border-radius: 50px;
    border: 2px solid lightgray;
    background-color: lightgoldenrodyellow;
    cursor: pointer;
    float : left;
    text-align: center;
}
</style>