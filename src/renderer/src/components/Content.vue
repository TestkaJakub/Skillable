<script setup lang="ts">
import YourSkills from './views/YourSkillsView.vue';
import Account from './views/AccountView.vue';
import Settings from './views/SettingsView.vue';
import About from './views/AboutView.vue';

const props = defineProps<{
    view: string
}>()


</script>

<template>
    <div id="content-pannel">
        <div id="general-view">
            <KeepAlive>
                <YourSkills v-if="props.view == 'Your Skills'" />
                <Account v-else-if="props.view == 'Account'" />
                <Settings v-else-if="props.view == 'Settings'" />
                <About v-else-if="props.view == 'About'" />
                <p v-else>Nothing to see here</p>
            </KeepAlive>
        </div>
    </div>
</template>
<style scoped>
#general-view {
    width: 80%;
}
</style>