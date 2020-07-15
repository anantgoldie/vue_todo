<template>
  <div class="todo-item">
    <p v-bind:class="{'is-complete':todo.isCompleted}">
      <input type="checkbox" v-on:change="markComplete" />
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.isCompleted = !this.todo.isCompleted;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  border-bottom: 1px #ccc dotted;
  padding: 10px;
  text-align: left;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background-color: red;
  padding: 5px 10px;
  color: white;
  border-radius: 50%;
  border: none;
  float: right;
  cursor: pointer;
}
</style>