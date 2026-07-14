<script setup>
import { ref, nextTick } from 'vue'

const activeService = ref(1)

const services = ref([
  {
    id: 1,
    title: 'Backend Web Development',
    desc: 'Creating server-side and web architecture using Laravel, Node.js, or Go.',
    icon: 'M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01'
  },
  {
    id: 2,
    title: 'Frontend Web Development',
    desc: 'Creating responsive and interactive UI using Tailwind CSS, and Vue.js.',
    icon: 'M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z' 
  },
  {
    id: 3,
    title: 'Database Management',
    desc: 'Designing relational schema, optimizing queries, and managing databases using MySQL & PostgreSQL.',
    icon: 'M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4'
  }
])

const getZIndexClass = (id) => {
  if (activeService.value === id) return 'z-30'
  // Cek selisih jarak id item dengan id yang lagi aktif
  const diff = Math.abs(activeService.value - id)
  if (diff === 1) return 'z-20'
  return 'z-10'
}

const selectService = async (id, event) => {
  activeService.value = id
  
  if (event && event.currentTarget) {
    await nextTick()
    const item = event.currentTarget
    const container = item.parentElement 
    
    if (container) {
      const centerLeft = item.offsetLeft - (container.clientWidth / 2) + (item.clientWidth / 2)
      container.scrollTo({
        left: centerLeft,
        behavior: 'smooth'
      })
    }
  }
}
</script>

<template>
  <section id="services" class="scroll-mt-24">
    <div class="mb-10">
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

    <div class="relative flex flex-row justify-start lg:justify-center items-center py-8 lg:py-12 overflow-x-auto overflow-y-visible px-4 w-full custom-scrollbar">
      <div 
        v-for="(service, index) in services" 
        :key="service.id" 
        @click="selectService(service.id, $event)" 
        :class="[
          'cursor-pointer transition-all duration-500 ease-out rounded-2xl p-6 w-[280px] md:w-[320px] lg:w-1/3 flex flex-col shrink-0',
          index !== 0 ? '-ml-20 lg:ml-6' : '',
          getZIndexClass(service.id), /* <-- Panggil fungsinya di sini */
          activeService === service.id 
            ? 'scale-105 bg-slate-800 border border-blue-500 shadow-[0_0_30px_rgba(59,130,246,0.2)] opacity-100' 
            : 'scale-95 lg:scale-100 bg-slate-900 border border-slate-700 shadow-xl opacity-60 hover:opacity-100 hover:-translate-y-2'
        ]"
      >
        <div :class="['w-12 h-12 rounded-xl flex items-center justify-center mb-5 transition-colors duration-300 shrink-0', activeService === service.id ? 'bg-blue-500 text-white' : 'bg-slate-800 text-blue-500']">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
            <path stroke-linecap="round" stroke-linejoin="round" :d="service.icon" />
          </svg>
        </div>
        <h3 :class="['text-lg md:text-xl font-bold mb-2 transition-colors duration-300 leading-snug', activeService === service.id ? 'text-blue-400' : 'text-white']">
          {{ service.title }}
        </h3>
        <p :class="['text-sm leading-relaxed flex-grow transition-colors duration-300', activeService === service.id ? 'text-slate-200' : 'text-slate-400']">
          {{ service.desc }}
        </p>
      </div>
    </div>
  </section>
</template>
<style scoped>
.custom-scrollbar::-webkit-scrollbar { 
  height: 4px; 
}
.custom-scrollbar::-webkit-scrollbar-track { background: transparent; }
.custom-scrollbar::-webkit-scrollbar-thumb { background: #2b81f8; border-radius: 10px; }
.custom-scrollbar::-webkit-scrollbar-thumb:hover { background: #3b82f6; }
</style>