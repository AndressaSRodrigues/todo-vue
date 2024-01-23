<script setup>
import TodoList from './components/TodoList.vue';
</script>

<template>
  <div class="container">
    <img src="./assets/taskhublogo.png" class="logo" alt="TaskHub Logo" width="auto" />
    <TodoList title="Organize your daily tasks" />
  </div>
</template>

<style scoped>
* {
  background-color: #FFFFFF;
  width: 60vw;
  height: 80vh;
  border: none;
  border-radius: 2em;
}

.container {
  margin: 2em;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.logo {
  width: 30vw;
  height: auto;
  padding: 2em 0 0 0;
  margin-top: 2em;
}
</style>
