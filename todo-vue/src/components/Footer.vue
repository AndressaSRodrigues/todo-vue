<script setup>
import gitHubIcon from '../assets/githubicon.png'
import likedinIcon from '../assets/linkedin.png'
import cvIcon from '../assets/cv.png'
</script>

<template>
    <footer>
        <a href="https://github.com/AndressaSRodrigues"><img :src="gitHubIcon" alt="GitHub" class="icon" /></a>
        <a href="https://www.linkedin.com/in/andressa-webdev/"><img :src="likedinIcon" alt="Linkedin" class="icon" /></a>
        <a href="https://flowcv.com/resume/0p0cbjhncd"><img :src="cvIcon" alt="Resume" class="icon" /></a>
    </footer>
</template>

<style scoped>
footer {
    width: 100%;
    margin: 5rem 0 0 0;
    background-color: #420077;
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: 10px;
}

.icon {
    width: 28px;
    padding-top: 10px;
}
</style>