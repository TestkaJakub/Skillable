<script setup lang="ts">
const props = defineProps<{
    view: string
}>()


</script>

<template>
    <div id="content-pannel">
        TO DO:
        <ul>
            <li>{{props.view}}</li>
        </ul>
    </div>
</template>
