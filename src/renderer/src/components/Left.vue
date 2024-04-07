<script setup lang="ts">
import { ref } from 'vue';

const views = ref([
    { name: 'Your Skills', path: '/skills', isActive: true },
    { name: 'Account', path: '/account', isActive: false },
    { name: 'Options', path: '/options', isActive: false },
    { name: 'About', path: '/about', isActive: false }
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
    color: #c5c5c5;
    align-self: flex-start;
}
button.activefalse:hover {
    color: #f5f5f5;
}
.activetrue {
    color: #a2a2a2;
}
</style>