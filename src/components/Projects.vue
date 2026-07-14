<script setup>
import { ref } from 'vue'

const projects = ref([
  { id: 1, 
    title: 'Inventory Management', 
    desc: 'Website for inventory management to store all your item.', 
    tech: ['Laravel', 'Tailwind', 'PhP', 'Node.js'], 
    link: 'https://github.com/Ravelery/Nemira-Inventory.git'},
  { id: 2, 
    title: 'Task Manager', 
    desc: 'Website to manage your task and keep all tracks.', 
    tech: ['Vue.js', 'Tailwind', 'Node.js'], 
    link: '#' },
  { id: 3, 
    title: 'Calculator', 
    desc: 'A simple calculator app build on python.', 
    tech: ['Python', 'NumPy'], 
    link: 'https://github.com/Ravelery/Calculator.git' }
])

const getTechColor = (techName) => {
  const colors = {
    'Laravel': 'bg-red-500/10 text-red-400 border border-red-500/30',
    'PhP': 'bg-indigo-500/10 text-indigo-400 border border-indigo-500/30',
    'Vue.js': 'bg-emerald-500/10 text-emerald-400 border border-emerald-500/30',
    'Tailwind': 'bg-sky-500/10 text-sky-400 border border-sky-500/30',
    'Python': 'bg-yellow-500/10 text-yellow-400 border border-yellow-500/30',
    'NumPy': 'bg-blue-500/10 text-blue-400 border border-blue-500/30',
    'Node.js': 'bg-green-500/10 text-green-400 border border-green-500/30'
  }
  
  return colors[techName] || 'bg-slate-700 text-slate-300 border border-slate-600'
}
</script>

<template>
  <section id="projects" class="scroll-mt-24">
    <div class="mb-10">
      <h3 class="text-lg md:text-xl text-blue-500 font-semibold tracking-wide uppercase mb-2">
        Projects
      </h3>
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-4">
        <h2 class="text-xl md:text-2xl font-extrabold text-white tracking-tight">
          Projects I've worked on
        </h2>
      </div>
      <div class="w-full h-px bg-slate-800 mt-6"></div>
    </div>
    
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div v-for="project in projects" :key="project.id" class="bg-slate-800 rounded-xl p-6 shadow-lg border border-slate-700/50 flex flex-col justify-between hover:border-teal-500/50 hover:-translate-y-1 transition-all duration-300 group">
        <div>
          <h4 class="text-xl font-bold text-white mb-2 group-hover:text-teal-400 transition-colors">{{ project.title }}</h4>
          <p class="text-slate-400 text-sm mb-4">{{ project.desc }}</p>
        </div>
        
        <div class="flex flex-wrap gap-2 mt-4">
          <span v-for="tech in project.tech" :key="tech" :class="['text-xs font-semibold px-2.5 py-1 rounded', getTechColor(tech)]">
            {{ tech }}
          </span>
        </div>
        
        <div class="mt-4">
          <a v-if="project.link !== '#'" 
             :href="project.link" 
             target="_blank" 
             class="text-teal-400 hover:text-teal-500 text-sm font-medium transition-colors">
            View Project
          </a>
          <span v-else 
                class="text-slate-500 text-sm font-medium italic cursor-not-allowed">
            Project in progress
          </span>
        </div>

      </div>
    </div>
  </section>
</template>