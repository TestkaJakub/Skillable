<script setup lang="ts">
import { ref } from 'vue';

const views = ref([
    { name: 'Your Skills', isActive: true },
    { name: 'Account', isActive: false },
    { name: 'Settings', isActive: false },
    { name: 'About', isActive: false }
]);

const emit = defineEmits();

function changeView(view){
    views.value.forEach(v => {
        v.isActive = v.name === view.name;
    });
    emit('view-changes', view.name);
}
</script>

<template>
    <div id="left-pannel">
        <nav>
            <button v-for="view in views" :class="'active'+view.isActive" :key="view.name" @click="changeView(view)">{{ view.name }}</button>
        </nav>
    </div>
</template>

<style scoped>
nav {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    align-items: center;
}
button {
    background-color: transparent;
    border: none;
    cursor: pointer;
    font-size: 1.5rem;
    color: var(--text-color-unimportant);
    align-self: flex-start;

    transition: all 0.3s ease-out 0.175s ;
}
.activetrue {
  cursor: default;
  color: var(--secondary-color-hovered);
}
</style>