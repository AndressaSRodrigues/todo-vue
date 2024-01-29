<script setup>
import TodoList from './components/TodoList.vue';
</script>

<template>
  <main>
    <section>
      <h1>TaskHub</h1>
      <h2>Organize your daily tasks</h2>
    </section>

    <section>
      <TodoList />
    </section>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0 1em;
  text-align: center;
}

h1 {
  font-size: 4rem;
  color: #EE0077;
  margin-bottom: 0;
}

h2 {
  font-size: 1.2rem;
  margin: 0 0 3rem 0;
}
</style>
