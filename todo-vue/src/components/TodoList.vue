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

const hideCompleted = ref(false)

const filteredTodos = computed(() => {
    return hideCompleted.value
        ? todos.value.filter((el) => !el.done)
        : todos.value
})

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

    <form @submit.prevent="addTodo" class="task-form">
        <input v-model="newTodo" placeholder="Add a new task" class="add-task" />
        <button class="button-add">Add</button>
    </form>

    <ol class="list">
        <li v-for="todo in filteredTodos" :key="todo.id" class="list-items">
            <span :class="{ done: todo.done }">{{ todo.text }}</span>
            <div class="actions">
                <input type="checkbox" v-model="todo.done" class="check">
                <button @click="removeTodo(todo)" class="button-remove">x</button>
            </div>
        </li>
    </ol>

    <button @click="hideCompleted = !hideCompleted" class="button-hide">
        {{ hideCompleted ? 'Show All Tasks' : 'Hide Completed Tasks' }}
    </button>
</template>

<style scoped>
h1 {
    font-size: 1.5em;
    color: #EE0077;
}

.task-form {
    width: 65vw;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    padding: 0.5em;
}

.add-task {
    width: 82%;
    padding: 1em;
    color: #420077;
    background-color: #FFFFFF;
    border: 2px solid #420077;
    border-radius: 0.5em;
}

.button-add, .button-remove, .button-hide {
    border: none;
    border-radius: 0.5em;
}

.button-add {
    width: 4em;
    height: 3.5em;
    margin-left: 1em;
    background-color: #420077;
    font-weight: bold;
}

.list {
    width: 65vw;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 0.5em;
}

.list-items {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 1em;
    color: #420077;
    border: 1px solid #E4E4E4;
    border-radius: 0.5em;
    margin-bottom: 1em;
}

.actions {
    display: flex;
    flex-direction: row;
    justify-content: end;
    align-items: center;
    margin-right: 1em;
}

.check {
    appearance: none;
    width: 1.5em;
    height: 1.5em;
    border: 1px solid #EE0077;
    border-radius: 0.5em;
}

.check:checked {
    background-color: #EE0077;
}

.button-remove {
    width: 1.5em;
    height: 1.5em;
    background-color: #420077;
    margin-left: 1em;
    font-weight: bold;
}

.done {
    text-decoration: line-through;
}

.button-hide {
    width: 12em;
    height: 3em;
    background-color: #EE0077;
}

.button-hide:hover {
    background-color: #420077;
    cursor: pointer;
}
</style>