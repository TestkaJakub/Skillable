<script setup lang="ts">
import Upper from './components/Upper.vue';
import Left from './components/Left.vue'
import Content from './components/Content.vue'
import { ref } from 'vue';

const menuDisplay = ref(false);
const activeView = ref('Your Skills')

function menuDisplayUpdated(value) {
  menuDisplay.value = value;
}

function viewChanges(view) {
  activeView.value = view;
}

const root = document.querySelector(':root');

const currentTheme = ref(localStorage.getItem('theme') || 'dark-theme');
if (currentTheme.value === 'light-theme') root?.classList.add('light-theme');

if(currentTheme.value === 'light-theme' && !root?.classList.contains('light-theme'))
{
  root?.classList.add('light-theme');
}
else if(currentTheme.value === 'dark-theme' && root?.classList.contains('light-theme'))
{
  root?.classList.remove('light-theme');
}
</script>

<template>
  <div id="app">
    <Upper :active-view="activeView" @menu-display-updated="menuDisplayUpdated($event)" />
    <div id="main">
      <Transition name="slide-fade">
        <Left v-if="menuDisplay" @view-changes="viewChanges($event)"/>
      </Transition>
      <Content :view="activeView" />
    </div>
  </div>
</template>

<style scoped>
#app {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

#upper-pannel {
  width: 100%;
  height: 10%;
  display: flex;
  flex-direction: row;
  justify-content: left;
  align-items: center;
  padding: 1rem;
}

#main{
  display: flex;
  flex-direction: row;
  height: 100%;
  width: 100%;
}
#left-pannel {
  width: 30%;
  height: 100%;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: center;
}

#content-pannel {
  width: 100%;
  height: 100%;
  padding: 1rem;
  transition: all 10s ease-out; 
  display: flex;
  flex-direction: column;
  align-items: center;
}

.slide-fade-enter-active {
  transition: all 0.5s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(-20px);
  opacity: 0;
}

</style>
