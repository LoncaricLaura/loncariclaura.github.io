<script setup lang="ts">
import { Project } from '@types/project';

const props = defineProps({
  project: {
    type: Object as Project,
    required: true,
  },
})
</script>

<template>
    <div class="relative flex flex-col justify-between w-full h-auto min-h-[350px] bg-slate-300/50 pl-5 md:pl-8 pr-4 py-6">
        <div>
            <p class="absolute -top-6 md:-top-12 -left-2 md:-left-5 text-pink text-[50px] md:text-[80px] font-extrabold italic">{{ project.id }}</p>
            <p class="text-md md:text-xl text-gray-dark">{{ project.name }}</p>
            
            <p class="py-4">{{ project.desc}}</p>
        </div>

        <div class="h-[40%] md:h-[30%] flex flex-col justify-start">
            <div class="flex gap-x-4">
                <img src="/public/img/languages-icon.png" alt="Icon" class="w-auto h-5">
                <p>{{ project.tools.join(', ') }}</p>
            </div>
            <NuxtLink :to="project.github" class="flex gap-x-4 pt-4 break-all cursor-pointer" target="_blank">
                <img src="/public/img/github-icon.png" alt="Icon" class="w-6 h-6">
                <p>{{ project.github }}</p>
            </NuxtLink>
        </div>
    </div>
</template>