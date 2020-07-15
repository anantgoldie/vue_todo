<template>
  <div>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <todoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)" />
    </div>
  </div>
</template>

<script>
import todoItem from "./TodoItem";
export default {
  name: "Todos",
  components: {
    todoItem
  },
  props: ["todos"]
};
</script>

<style scoped>
</style>