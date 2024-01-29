<script setup>
import taskHubLogo from '../assets/taskhublogo.png'
</script>

<template>
<nav>
<img :src="taskHubLogo" alt="TaskHub Logo">
</nav>
</template>

<style scoped>
nav {
    width: 100%;
    height: 3rem;
    margin: 0;
    background-color: #420077;
    display: flex;
    flex-direction: row;
    justify-content: start;
    align-items: center;
    gap: 10px;
}

img {
    height: 1rem;
    margin-left: 1rem;
}
</style>