<script setup>
import { ref } from 'vue'

const isOpen = ref(false)
</script>

<template>
  <nav class="sticky top-0 z-50 bg-slate-900/80 backdrop-blur-md border-b border-slate-800">
    <div class="max-w-screen mx-auto px-6 py-4 flex justify-between items-center relative">
      
      <div class="font-bold text-3xl ps-px text-blue-500 tracking-wider">MyPortofolio<span class="text-white">.</span></div>
      
      <div class="hidden sm:flex gap-6 px-8 text-lg font-medium">
        <a href="#hero" class="hover:text-blue-400 transition-colors">Home</a>
        <a href="#info" class="hover:text-blue-400 transition-colors">Info</a>
        <a href="#stack" class="hover:text-blue-400 transition-colors">Stack</a>
        <a href="#services" class="hover:text-blue-400 transition-colors">Services</a>
        <a href="#projects" class="hover:text-blue-400 transition-colors">Projects</a>
        <a href="#contact" class="hover:text-blue-400 transition-colors">Contact</a>

      </div>

      <button @click="isOpen = !isOpen" class="sm:hidden text-slate-300 hover:text-white focus:outline-none transition-colors">
        <svg v-if="!isOpen" xmlns="http://www.w3.org/2000/svg" class="h-7 w-7" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-7 w-7" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>

      <transition name="pop-down">
        <div v-if="isOpen" class="sm:hidden absolute top-full right-6 mt-2 w-48 bg-slate-800/95 backdrop-blur-xl border border-slate-700 rounded-2xl shadow-2xl p-2 z-50">
          <div class="flex flex-col text-sm font-medium">
            <a href="#hero" @click="isOpen = false" class="block px-4 py-3 rounded-xl hover:bg-slate-700 hover:text-blue-400 transition-all text-left">Home</a>
            <a href="#info" @click="isOpen = false" class="block px-4 py-3 rounded-xl hover:bg-slate-700 hover:text-blue-400 transition-all text-left">Info</a>
            <a href="#stack" @click="isOpen = false" class="block px-4 py-3 rounded-xl hover:bg-slate-700 hover:text-blue-400 transition-all text-left">Stack</a>
            <a href="#services" @click="isOpen = false" class="block px-4 py-3 rounded-xl hover:bg-slate-700 hover:text-blue-400 transition-all text-left">Services</a>
            <a href="#projects" @click="isOpen = false" class="block px-4 py-3 rounded-xl hover:bg-slate-700 hover:text-blue-400 transition-all text-left">Projects</a>
            <a href="#contact" @click="isOpen = false" class="block px-4 py-3 rounded-xl hover:bg-slate-700 hover:text-blue-400 transition-all text-left">Contact</a>

          </div>
        </div>
      </transition>

    </div>
  </nav>
</template>

<style scoped>
.pop-down-enter-active,
.pop-down-leave-active {
  transition: opacity 0.2s ease, transform 0.2s ease;
}
.pop-down-enter-from,
.pop-down-leave-to {
  opacity: 0;
  transform: translateY(-10px) scale(0.95);
}
</style>