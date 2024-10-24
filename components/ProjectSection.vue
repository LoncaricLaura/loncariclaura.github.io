<script lang="ts" setup>
import { ref, computed } from 'vue';
import { Project } from '@types/project';
import {projects} from '/public/docs/projects.json'

const myProjects = ref([] as Project[]);

onMounted(() => {
    myProjects.value = projects;
})
</script>

<template>
    <div id="projects" class="flex flex-col items-center pt-12 md:pt-24 px-4 md:px-16 lg:px-24 xl:px-32 w-full">
        <h2 class="text-3xl text-gray-400 pb-12">MY PROJECTS</h2>
        <div v-if="myProjects" class="grid grid-cols-1 sm:grid-cols-2 gap-10 justify-around w-full xl:w-[90%]">
            <ProjectCard v-for="project in myProjects" :key="project.id" :project="project" />
        </div>
    </div>
</template>