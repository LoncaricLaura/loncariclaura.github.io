<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue';
import { scrollToSection } from '/composables/scrollToSection.ts'

const isMenuOpen = ref(false);
const isScrolled = ref(false);

const toggleMobMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
};

const handleScroll = () => {
    isScrolled.value = window.scrollY > 100;
};

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
});

onBeforeUnmount(() => {
    window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
    <main class="fixed z-40 top-0 h-fit w-full transition-colors duration-300">
        <div :class="[
            'hidden sm:flex flex-row justify-end gap-6 md:gap-12 px-4 md:px-16 lg:px-24 xl:px-32 py-4 w-full text-xl text-zinc-400 md:text-gray',
            isScrolled ? 'main bg-gradient-to-r from-transparent to-[#020102]' : 'bg-transparent'
        ]">
            <p class="cursor-pointer" @click="scrollToSection('about')">About</p>
            <p class="cursor-pointer" @click="scrollToSection('projects')">Projects</p>
        </div>

        <div class="absolute right-4 sm:hidden flex justify-end items-center py-6 z-50">
            <button class="btn ml-4 flex flex-col" aria-label="Menu" @click="toggleMobMenu">
                <div class="hamb-line m-0.5 h-0.5 w-6 bg-[#e8f0fa] transition-all duration-300" :class="[isMenuOpen ? 'translate-y-[5px] rotate-45' : '']" />
                <div class="hamb-line m-0.5 h-0.5 w-6 bg-[#e8f0fa] transition-all duration-300" :class="[isMenuOpen ? 'opacity-0' : '']" />
                <div class="hamb-line m-0.5 h-0.5 w-6 bg-[#e8f0fa] transition-all duration-300" :class="[isMenuOpen ? 'translate-y-[-7px] -rotate-45' : '']" />
            </button>
        </div>

        <MobileMenu v-if="isMenuOpen" @toggleMobMenu="toggleMobMenu" />
    </main>
</template>

<style scoped>
.main {
  transition: background-color 0.5s ease-out;
}
</style>
