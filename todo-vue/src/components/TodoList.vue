<script setup>
import { ref } from 'vue';

defineProps({
    title: String
})

const newTodo = ref('')

</script>

<template>
    <h1>{{ title }}</h1>
    <form class="new-task-form">
        <input v-model="newTodo" placeholder="Add a new task"/>
        <button>Add</button>
    </form>
</template>

<style scoped>
h1 {
    font-size: 1.5em;
    color: #83C0C1;
}

.new-task-form {
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin-top: 2em;
}

input {
    width: 22em;
    padding: 1em;
    color: #6C22A6;
    background-color: #FFFFFF;
    border: 2px solid #B461D9;
    border-radius: 0.5em;
}

button {
    width: 4em;
    margin-left: 1em;
    border: none;
    border-radius: 0.5em;
    background-color: #B461D9;
    font-weight: bold;
}

</style>