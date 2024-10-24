<script setup>
import { useRouter } from 'vue-router'
import { ref } from 'vue'
import { scrollToSection } from '/composables/scrollToSection.ts'

const emit = defineEmits(['toggleMobMenu'])

const handleClick = (id) => {
  scrollToSection(id);
  emit('toggleMobMenu')
}
</script>

<template>
    <main class="absolute z-40 top-0 left-0 w-full h-screen sm:hidden flex flex-col items-center justify-start gap-y-5 bg-[#020102]/95 px-4 py-24">
      <div class="flex flex-col items-start justify-center gap-y-6 cursor-pointer text-[#d4a9b0] text-xl">
        <p class="cursor-pointer" @click="handleClick('about')">About</p>
        <p class="cursor-pointer" @click="handleClick('projects')">Projects</p>
      </div>
    </main>
  </template>
    