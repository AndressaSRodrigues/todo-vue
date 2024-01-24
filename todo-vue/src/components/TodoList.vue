<script setup>
import { computed, ref } from 'vue';

defineProps({
    title: String
})

const newTodo = ref('')

let id = 0

const todos = ref([
    { id: id++, text: 'You can add, edit or remove tasks. Try it out.', done: false }
])

function addTodo() {
    todos.value.push({ id: id++, text: newTodo.value, done: false })
    newTodo.value = ''
}

function removeTodo(todo) {
    todos.value = todos.value.filter((el) => el !== todo)
}

</script>

<template>
    <h1>{{ title }}</h1>
    <form class="new-task-form" @submit.prevent="addTodo">
        <input v-model="newTodo" placeholder="Add a new task" />
        <button>Add</button>
    </form>

    <ul class="todo-list">
        <li v-for="todo in todos" :key="todo.id">
            <input type="checkbox" v-model="todo.done">
            <span :class="{ done: todo.done }">{{ todo.text }}</span>
            <button @click="removeTodo(todo)">X</button>
        </li>
    </ul>
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

.todo-list {
    color: #6C22A6;
    list-style: none;
}

input[type="checkbox"] {
    appearance: none;
    width: 20px;
    margin-right: 20px;
    background-color: #fff;
}

input[type="checkbox"]:checked {
    background-color: #83C0C1;
}

.done {
    text-decoration: line-through;
}
</style>