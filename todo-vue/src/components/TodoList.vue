<script setup>
import { computed, ref, watch, onMounted } from 'vue';

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

watch(todos, newVal => {
    localStorage.setItem('todos', JSON.stringify(newVal))
}, { deep: true })

onMounted(() => {
    const storedTodos = JSON.parse(localStorage.getItem('todos')) || [];
    todos.value = storedTodos;
});

</script>

<template>
    <section>
        <form @submit.prevent="addTodo" class="tasks-form">
            <input v-model="newTodo" placeholder="Add a new task" class="add-input" />
            <button class="add-button" :disabled="newTodo.trim() === ''">ADD</button>
        </form>

        <ul class="todos-list">
            <li v-for="todo in filteredTodos" :key="todo.id" class="list-item">
                <p :class="{ done: todo.done }">{{ todo.text }}</p>
                <div class="actions">
                    <input type="checkbox" v-model="todo.done">
                    <button @click="removeTodo(todo)" class="delete-task">Delete</button>
                </div>
            </li>
        </ul>

        <button @click="hideCompleted = !hideCompleted" class="hide-button">
            {{ hideCompleted ? 'Show All Tasks' : 'Hide Completed Tasks' }}
        </button>
    </section>
</template>

<style scoped>
.tasks-form {
    width: 90vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 5px;
}

.add-input {
    padding: 1rem;
    border: 1px solid #EE0077;
    border-radius: 4px;
}

.add-button,
.hide-button {
    padding: 0.5rem;
    background-color: #EE0077;
    border: 1px solid #EE0077;
    border-radius: 4px;
    color: #EEEEEE;
    font-weight: bold;
    cursor: pointer;
}

.hide-button:hover,
.add-button:hover {
    background-color: #420077;
}

.add-button:disabled,
.add-button:disabled:hover {
    background-color: #EEEEEE;
    color: darkgrey;
    border: none;
    cursor: not-allowed;
}

.todos-list {
    padding: 0;
    text-align: start;
    margin-top: 2rem;
}

.list-item {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    gap: 10px;
    border: 1px solid #EEEEEE;
    border-radius: 5px;
    padding: 0.5rem;
    margin: 5px 0;
}

.list-item p {
    width: 100%;
}

.actions {
    display: flex;
    flex-direction: row;
    gap: 10px;
    align-items: center;
}

input[type='checkbox'] {
    width: 20px;
    height: 20px;
    color: #EEEEEE;
    accent-color: #9DBC98;
}

.delete-task {
    width: 45px;
    height: 22px;
    background-color: #FF6868;
    border: none;
    border-radius: 2px;
    font-size: 10px;
    font-weight: 600;
    color: #EEEEEE;
}

.hide-button {
    width: 100%;
    margin: 10px 0 20px 0;
}

@media screen and (min-width: 800px) {
    .tasks-form {
        width: 60vw;
        flex-direction: row;
    }

    .add-input {
        width: 100%;
    }

    .add-button {
        width: 10%;
    }

    .hide-button {
        width: 20%;
    }
}
</style>