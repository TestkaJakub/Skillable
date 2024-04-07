<script setup lang="ts">
import { ref } from 'vue';

const menuDisplay = ref(false);

const emit = defineEmits();

function toggleMenu() {
    menuDisplay.value = !menuDisplay.value;
    emit('menu-display-updated', menuDisplay.value);
}
</script>

<template>
    <div id="upper-pannel">
        <div id="app-intro">
            <img src="..\assets\placeholderlogo.svg" alt="Skillable Logo" id="logo"/>
            <h1>Skillable</h1>
            <button id="menu-display-button" @click="toggleMenu()">
                <h2>≡</h2>
            </button>
        </div>
    </div>
</template>

<style scoped>
#app-intro {
    display: flex;
    flex-direction: row;
    gap: 1rem;
    align-items: center;
}
#menu-display-button {
    background-color: transparent;
    border: none;
    cursor: pointer;
    font-size: 2rem;
    color: #c5c5c5;
}
</style>