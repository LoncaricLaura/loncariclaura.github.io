<script setup>
import { useRouter } from 'vue-router'
import { ref } from 'vue'

const props = defineProps({
  isMenuOpen: {
    type: Boolean,
    required: true,
  },
})
</script>

<template>
    <main class="absolute z-40 top-0 left-0 w-full h-screen sm:hidden flex flex-col items-center justify-start gap-y-5 bg-[#020102]/95 px-4 py-24">
      <div @click="isMenuOpen = !isMenuOpen" class="flex flex-col items-start justify-center gap-y-6 cursor-pointer text-[#d4a9b0] text-xl">
        <NuxtLink to="/" class="cursor-pointer">About</NuxtLink>
        <NuxtLink to="/" class="cursor-pointer">Projects</NuxtLink>
        <NuxtLink to="/" class="cursor-pointer">Contact</NuxtLink>
      </div>
    </main>
  </template>
    