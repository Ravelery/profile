<script setup>
import { ref } from 'vue'

const services = ref([
  {
    id: 1,
    title: 'Backend Web Development',
    desc: 'Membangun arsitektur server-side yang tangguh, aman, dan efisien menggunakan Laravel, Node.js, atau Go.',
    icon: 'M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01'
  },
  {
    id: 2,
    title: 'Frontend Web Development',
    desc: 'Membangun antarmuka pengguna yang responsif dan interaktif menggunakan Tailwind CSS, dan Vue.js.',
    icon: 'M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z' 
  },
  {
    id: 3,
    title: 'Database Management',
    desc: 'Merancang skema relasional, optimasi query, dan manajemen database menggunakan MySQL & PostgreSQL.',
    icon: 'M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4' // Icon Database
  }
])
</script>

<template>
  <section id="services" class="scroll-mt-24">
    <div class="mb-8">
      <h3 class="text-lg md:text-xl text-blue-500 font-semibold tracking-wide uppercase mb-2">
        Services
      </h3>
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-4">
        <h2 class="text-xl md:text-2xl font-extrabold text-white tracking-tight">
          My areas of expertise!
        </h2>
        <a href="#projects" class="text-slate-400 text-sm hover:text-blue-400 transition-colors font-medium flex items-center gap-1 group">
          View my work 
          <span class="group-hover:translate-x-1 transition-transform">→</span>
        </a>
      </div>
      <div class="w-full h-px bg-slate-800 mt-5"></div>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
      <div 
        v-for="service in services" 
        :key="service.id" 
        class="w-full sm:w-[500px] bg-slate-900/50 p-5 rounded-2xl border border-slate-800 hover:border-blue-500/50 hover:bg-slate-800/80 transition-all duration-300 group flex flex-col shrink-0"
      >
        <div class="w-12 h-12 bg-slate-800 text-blue-500 rounded-xl flex items-center justify-center mb-4 group-hover:bg-blue-500 group-hover:text-white transition-colors duration-300 shrink-0">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
            <path stroke-linecap="round" stroke-linejoin="round" :d="service.icon" />
          </svg>
        </div>
        <h3 class="text-lg font-bold text-white mb-2 group-hover:text-blue-400 transition-colors leading-snug">
          {{ service.title }}
        </h3>
        <p class="text-slate-400 text-sm leading-relaxed flex-grow">
          {{ service.desc }}
        </p>
      </div>
    </div>
  </section>
</template>