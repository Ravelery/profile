<script setup>
import { ref } from 'vue'

const activeTech = ref('Vscode')
const techContent = {
  Vscode: { name: 'Visual Studio Code', desc: 'My primary code editor for development.', icon: 'https://skillicons.dev/icons?i=vscode' },
  git: { name: 'Git', desc: 'Version control system for tracking changes in source code during development.', icon: 'https://skillicons.dev/icons?i=git' },
  github: { name: 'GitHub', desc: 'Platform for version control and collaboration.', icon: 'https://skillicons.dev/icons?i=github' },
  docker: { name: 'Docker', desc: 'Platform for containerizing applications.', icon: 'https://skillicons.dev/icons?i=docker' },
  mysql: { name: 'MySQL', desc: 'Relational database management system.', icon: 'https://skillicons.dev/icons?i=mysql' },
  postgresql: { name: 'PostgreSQL', desc: 'Advanced open-source relational database.', icon: 'https://skillicons.dev/icons?i=postgresql' },
  redis: { name: 'Redis', desc: 'In-memory data structure store, used as a database, cache, and message broker.', icon: 'https://skillicons.dev/icons?i=redis' },
  npm: { name: 'npm', desc: 'Package manager for Node.js and dependencies management.', icon: 'https://skillicons.dev/icons?i=npm' },
  postman: { name: 'Postman', desc: 'API development and testing tool.', icon: 'https://skillicons.dev/icons?i=postman' }   
}

const selectTech = (key, event) => {
  activeTech.value = key
  
  if (event && event.currentTarget) {
    event.currentTarget.scrollIntoView({
      behavior: 'smooth',
      inline: 'center',
      block: 'nearest'
    })
  }
}
</script>

<template>
  <section id="tool" class="scroll-mt-24">
    <h3 class="text-2xl font-bold mb-6 flex items-center gap-3">
      <span class="w-8 h-1 bg-cyan-500 rounded-full"></span>Tools
    </h3>
    
    <div class="bg-slate-800 p-6 md:p-8 rounded-3xl border border-slate-700 flex flex-col gap-8 items-center">
      
      <div class="flex flex-nowrap overflow-x-auto gap-6 w-full pb-6 pt-2 px-4 snap-x snap-mandatory custom-scrollbar">
        <button 
          v-for="(tech, key) in techContent" 
          :key="key" 
          @click="selectTech(key, $event)" 
          :class="activeTech === key ? 'scale-110 ring-4 ring-cyan-500 rounded-xl' : 'scale-100 opacity-60 hover:opacity-100 hover:scale-105'" 
          class="transition-all duration-300 shrink-0 snap-center origin-center">
          <img :src="tech.icon" :alt="tech.name" class="w-16 h-16 sm:w-20 sm:h-20 rounded-xl" />
        </button>
      </div>

      <div class="bg-slate-900 p-8 rounded-2xl border border-slate-700 w-full min-h-[140px] flex items-center justify-center text-center">
        <transition name="fade" mode="out-in">
          <div :key="activeTech">
            <h4 class="text-2xl font-bold text-cyan-400 mb-3">{{ techContent[activeTech].name }}</h4>
            <p class="text-slate-300 text-lg max-w-2xl mx-auto">{{ techContent[activeTech].desc }}</p>
          </div>
        </transition>
      </div>
      
    </div>
  </section>
</template>
<style scoped>
.fade-enter-active, .fade-leave-active { transition: opacity 0.2s ease; }
.fade-enter-from, .fade-leave-to { opacity: 0; }

.custom-scrollbar::-webkit-scrollbar {
  height: 6px; 
}
.custom-scrollbar::-webkit-scrollbar-track {
  background: #1e293b; 
  border-radius: 10px;
}        
.custom-scrollbar::-webkit-scrollbar-thumb {
  background: #3b82f6; 
  border-radius: 10px;
}
.custom-scrollbar::-webkit-scrollbar-thumb:hover {
  background: #60a5fa; 
}
</style>