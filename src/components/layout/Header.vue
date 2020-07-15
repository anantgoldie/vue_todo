<template>
  <header class="header">
    <h1>Todos</h1>
    <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "todoHeader"
};
</script>

<style>
.header {
  background: black;
  color: white;
  text-align: center;
  padding: 10px;
}

.header a {
  color: white;
  padding-right: 5px;
}
</style>