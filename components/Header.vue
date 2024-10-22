<script setup lang="ts">
const isMenuOpen = ref(false);

const toggleMobMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
}
</script>

<template>
    <main class="absolute z-40 top-0 max-h-10 h-full w-full">
        <div class="hidden sm:flex flex-row justify-end gap-6 md:gap-12 px-4 md:px-16 lg:px-24 xl:px-32 pt-6 w-full text-xl text-zinc-400 md:text-gray">
            <p class="cursor-pointer">About</p>
            <p class="cursor-pointer">Projects</p>
            <p class="cursor-pointer">Contact</p>
        </div>

        <div class="absolute right-4 sm:hidden flex justify-end items-center py-6 z-50">
            <button class="btn ml-4 flex flex-col" aria-label="Menu" @click=toggleMobMenu>
                <div class="hamb-line m-0.5 h-0.5 w-6 bg-[#e8f0fa] transition-all duration-300" :class="[isMenuOpen ? 'translate-y-[5px] rotate-45' : '']" />
                <div class="hamb-line m-0.5 h-0.5 w-6 bg-[#e8f0fa] transition-all duration-300" :class="[isMenuOpen ? 'opacity-0' : '']" />
                <div class="hamb-line m-0.5 h-0.5 w-6 bg-[#e8f0fa] transition-all duration-300" :class="[isMenuOpen ? 'translate-y-[-7px] -rotate-45' : '']" />
            </button>
        </div>

    <MobileMenu v-if="isMenuOpen" :isMenuOpen="isMenuOpen" /> 
    </main>
</template>