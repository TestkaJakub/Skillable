<script setup lang="ts">
import { Ref, ref } from 'vue';

class Skill {
    name: string;
    constructor(name) {
        this.name = name;
    }

    removeSkill() {
        skills.value = skills.value.filter(skill => skill !== this);
    }
}

const skills : Ref<Skill[]> = ref([]);

function createSkill() {
    const name = (document.querySelector('.add-skill input')as HTMLInputElement).value;
    if(name === '') return;
    skills.value.push(new Skill(name));
}

</script>

<template>
    <div class="skill-list">
        <div class="skill" v-for="skill in skills">
            <h3>{{ skill.name }}</h3>
            <button @click="skill.removeSkill()">Remove</button>
        </div>
    </div>
    <div class="add-skill">
        <input type="text" placeholder="Skill name"/>
        <button @click="createSkill()">Add Skill</button>
    </div>
</template>