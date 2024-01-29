<script setup>
import TodoList from './components/TodoList.vue';
import Footer from './components/Footer.vue';
import Navbar from './components/Navbar.vue';
import mainImg from './assets/taskhubmain.jpg'
</script>

<template>
  <Navbar/>
  <main>
    <section>
      <img :src="mainImg" alt="Two people organizing their tasks" width="80%">
      <h2>Organize your daily tasks</h2>
    </section>

    <section>
      <TodoList />
    </section>
  </main>
  <Footer/>
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

@media screen and (min-width: 800px) {
  main {
    padding: 0 25rem;
  }
}
</style>
