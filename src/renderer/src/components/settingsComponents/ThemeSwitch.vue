<script setup lang="ts">
import { ref } from 'vue';

const root = document.querySelector(':root');

const currentTheme = ref(localStorage.getItem('theme') || 'dark-theme');
if (currentTheme.value === 'light-theme') root?.classList.add('light-theme');

function changeTheme()
{
  if (root){
    root.classList.toggle('light-theme');

    currentTheme.value = root.classList.contains('light-theme') ? 'light-theme' : 'dark-theme';
    localStorage.setItem('theme', currentTheme.value);
  }
}
</script>

<template>
    <div class="themeswitch">
        <button class="theme-button settings-button" @click="changeTheme()">
            Switch to {{ currentTheme == 'light-theme' ? 'Darkmode' : 'Lightmode' }}
        </button>
    </div>   
</template>

<style scoped>
button {
    justify-content: center;
    align-items: center;
    border-radius: 0.5rem;
    font-size: 1.5rem;
    cursor: pointer;
    transition: all 0.3s ease-out 0.175s;
}
.themeswitch {
    display: flex;
    flex-direction: column;
}

</style>