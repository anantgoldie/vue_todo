<template>
  <div id="app">
    <addTodo v-on:add-todo="addTodo" />
    <todos v-bind:todos="todos" v-on:del-todo="delTodo" />
  </div>
</template>

<script>
import todos from "../components/Todos";
import addTodo from "../components/AddTodo";
import axios from "axios";

export default {
  name: "Home",
  components: {
    addTodo,
    todos
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    delTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => {
          console.log(res.data);
          this.todos = this.todos.filter(todos => todos.id != id);
        });
    },
    addTodo(newTodo) {
      const { title, isCompleted } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title: title,
          isCompleted: isCompleted
        })
        .then(res => {
          console.log(newTodo);
          this.todos = [...this.todos, res.data];
        })
        .catch(err => console.log(err));
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err));
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  line-height: 1.4;
  font-family: Arial, Helvetica, sans-serif;
}

.btn {
  display: inline-block;
  border: none;
  background-color: #555;
  color: white;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background-color: #666;
}
</style>
