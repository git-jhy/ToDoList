<template>
  <div id="#app">
    <p id="title">TodoList</p>
    <div>
      <input type="text" v-model="inputValue">
      <button @click="handleSubmit">add</button>
    </div>
    <ul>
      <todo-item v-for="(item, index) of todos"
      :key="index"
      :content="item"
      :index="index"
      @delete="handelDelete"></todo-item>
    </ul>
  </div>
</template>

<script>
import Todoitem from './components/Todoitem'
export default {
  data: function () {
    return {
      inputValue: '',
      todos: []
    }
  },
  components: {
    'todo-item': Todoitem
  },
  methods: {
    handleSubmit: function () {
      for (let item of this.todos) {
        if (this.inputValue.trim() === item) {
          return
        }
      }
      this.todos.push(this.inputValue.trim())
      this.inputValue = ''
    },
    handelDelete: function (index) {
      this.todos.splice(index, 1)
    }
  }
}
</script>

<style>
body {
  background-color: rgb(255, 237, 237);
  margin-top: 100px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

#title {
  font-size: 2em;
  margin-left: 10px;
  color: rgb(255, 98, 98);
  font-weight: bold;
  text-shadow: rgb(193, 175, 175) 5px 4px 6px;
}

ul {
  padding-left: 0;
  margin-left: 0;
  text-align: center;
  justify-content: center;
}

input {
  width: 200px;
  height: 32px;
  border: 2px solid #ccc;
  border-radius: 10px;
  font-size: 1.1em;
  outline: none;
}

button {
  font-size: 1em;
  width: 50px;
  height: 36px;
  outline: none;
  border-radius: 8px;
  border: 2px solid #ccc;
}

button:hover {
  color: rgb(30, 151, 81);
}
</style>
