<script setup>
import { ref } from 'vue'

const activeTech = ref('Vscode')
const techContent = {
  Vscode: { 
    name: 'Visual Studio Code', 
    desc: 'My primary code editor for development.', 
    icon: 'https://skillicons.dev/icons?i=vscode' },
  git: { 
    name: 'Git', 
    desc: 'Version control system for tracking changes in source code during development.', 
    icon: 'https://skillicons.dev/icons?i=git' },
  github: { 
    name: 'GitHub', 
    desc: 'Platform for version control and collaboration.', 
    icon: 'https://skillicons.dev/icons?i=github' },
  mysql: { 
    name: 'MySQL', 
    desc: 'Relational database management system.', 
    icon: 'https://skillicons.dev/icons?i=mysql' },
  postgresql: { 
    name: 'PostgreSQL', 
    desc: 'Advanced open-source relational database.', 
    icon: 'https://skillicons.dev/icons?i=postgresql' },
  npm: { 
    name: 'npm', 
    desc: 'Package manager for Node.js and dependencies management.', 
    icon: 'https://skillicons.dev/icons?i=npm' },
  postman: { 
    name: 'Postman', 
    desc: 'API development and testing tool.', 
    icon: 'https://skillicons.dev/icons?i=postman' }   
}

const selectTech = (key, event) => {
  activeTech.value = key
  
  if (event && event.currentTarget) {
    const button = event.currentTarget
    const container = button.parentElement
    
    const buttonRect = button.getBoundingClientRect()
    const containerRect = container.getBoundingClientRect()
    
    const scrollY = container.scrollTop + (buttonRect.top - containerRect.top) - (container.clientHeight / 2) + (buttonRect.height / 2)
    const scrollX = container.scrollLeft + (buttonRect.left - containerRect.left) - (container.clientWidth / 2) + (buttonRect.width / 2)
    
    container.scrollTo({
      top: scrollY,
      left: scrollX,
      behavior: 'smooth'
    })
  }
}
</script>

<template>
  <section id="stack" class="scroll-mt-24">
        <div class="mb-10">
      <h3 class="text-2xl md:text-3xl text-mist-200 font-semibold tracking-wide uppercase mb-2">
        Tools 
      </h3>
      <div class="w-full h-px bg-slate-800 mt-6"></div>
    </div>
    <div class="bg-slate-800 rounded-3xl border border-slate-700 flex flex-col md:flex-row overflow-hidden shadow-xl min-h-[400px]">
      
<div class="flex-1 p-8 md:p-10 flex flex-col justify-start">
  <div class="mb-6 text-left shrink-0">
    <h3 class="text-blue-500 font-semibold text-xl mb-1 tracking-wide">Tools</h3>
    <h2 class="text-3xl md:text-4xl font-extrabold text-white tracking-tight">tool i use on developmet</h2>
  </div>
  
  <hr class="border-slate-600 mb-8 shrink-0" />

  <div class="flex-1 flex flex-col justify-center">
    <transition name="fade" mode="out-in">
      <div :key="activeTech">
        <div class="flex flex-col sm:flex-row sm:items-center gap-4 sm:gap-6 mb-6">
          <h3 class="text-3xl md:text-4xl font-bold text-white min-w-[140px]">{{ techContent[activeTech].name }}</h3>
        </div>
        <p class="text-slate-300 text-base md:text-lg leading-relaxed max-w-xl">
          {{ techContent[activeTech].desc }}
        </p>
      </div>
    </transition>
  </div>
</div>

      <div class="w-full md:w-36 shrink-0 p-4 flex flex-row md:flex-col overflow-x-auto md:overflow-y-auto md:overflow-x-hidden gap-4 items-center snap-x md:snap-y snap-mandatory custom-scrollbar border-t md:border-t-0 md:border-l border-slate-700 h-[120px] md:h-auto md:max-h-[450px]">
        <button 
          v-for="(tech, key) in techContent" 
          :key="key" 
          @click="selectTech(key, $event)" 
          :class="activeTech === key ? 'ring-2 ring-blue-500 rounded-xl' : 'opacity-50 hover:opacity-100 hover:scale-105'" 
          class="transition-all duration-300 shrink-0 snap-center origin-center p-2">
          <img :src="tech.icon" :alt="tech.name" class="w-20 h-20 md:w-24 md:h-24 rounded-lg object-contain" />
        </button>
      </div>

    </div>
  </section>
</template>

<style scoped>
.fade-enter-active, .fade-leave-active { transition: opacity 0.3s ease; }
.fade-enter-from, .fade-leave-to { opacity: 0; }

.custom-scrollbar::-webkit-scrollbar { 
  width: 6px;
  height: 6px; 
}
.custom-scrollbar::-webkit-scrollbar-track { 
  background: transparent; 
}
.custom-scrollbar::-webkit-scrollbar-thumb { 
  background: #67a6ff; 
  border-radius: 10px; 
}
.custom-scrollbar::-webkit-scrollbar-thumb:hover { 
  background: #3b82f6; 
}
</style>