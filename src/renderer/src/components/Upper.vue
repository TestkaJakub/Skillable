<script setup lang="ts">
import { ref } from 'vue';

const menuDisplay = ref(false);

const props = defineProps<{
   activeView: string;
}>();

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
        <div id="app-view-info">
            <h2>Active tab: {{ props.activeView }}</h2>
        </div>
    </div>
</template>

<style scoped>
#app-intro {
    display: flex;
    flex-direction: row;
    gap: 1rem;
    align-items: center;
    width: min-content;
}
#menu-display-button {
    background-color: transparent;
    border: none;
    cursor: pointer;
    font-size: 2rem;
}
@media screen and (min-width: 992px) {
    #app-view-info {
        flex: 0 1 auto;
        height: 100px;
        position: absolute;
        left: 50%;
        transform: translateX(-50%) translateY(23%);
    }
}
@media screen and (max-width: 992px) {
    #app-view-info {
        align-content: center;
    }
}

#logo {
    filter: invert(54%) sepia(96%) saturate(217%) hue-rotate(132deg) brightness(91%) contrast(87%);
}

.light-theme #logo {
    filter: invert(45%) sepia(11%) saturate(4789%) hue-rotate(356deg) brightness(87%) contrast(80%);
}
</style>