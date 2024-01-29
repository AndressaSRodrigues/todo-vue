<script setup>
import TodoList from './components/TodoList.vue';
</script>

<template>
  <div class="container">
    <img src="./assets/taskhub-logo.png" class="logo" alt="TaskHub Logo" width="auto" />
    <TodoList title="Organize your daily tasks" />
  </div>
</template>

<style scoped>
* {
  background-color: #FFFFFF;
  width: 65vw;
  height: fit-content;
  padding: 2em;
  border: none;
  border-radius: 1em;
}

.container {
  margin: 2em;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.logo {
  width: 50vw;
  height: auto;
  padding: 2em 0 0 0;
}
</style>
