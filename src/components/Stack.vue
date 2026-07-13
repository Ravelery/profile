<script setup>
import { ref } from 'vue'

const activeTech = ref('laravel')

const techContent = {
  laravel: { 
    name: 'Laravel', 
    skill: 80,
    color: 'bg-red-500',
    desc: 'My primary stack for building websites and complex systems for websites also to handle backend logic.', 
    icon: 'https://skillicons.dev/icons?i=laravel' 
  },
  python: { 
    name: 'Python', 
    skill: 75,
    color: 'bg-yellow-500',
    desc: 'Secondary stack for automation, data processing and management also for making APIs quick and efficient.', 
    icon: 'https://skillicons.dev/icons?i=python' 
  },
  node: { 
    name: 'Node.js', 
    skill: 50,
    color: 'bg-green-500',
    desc: 'Support stack used for real-time systems and scalable backend architectures.', 
    icon: 'https://skillicons.dev/icons?i=nodejs' 
  },
  php: { 
    name: 'PHP', 
    skill: 80,
    color: 'bg-indigo-400',
    desc: 'Language use on laravel used for server-side scripting and web development.', 
    icon: 'https://skillicons.dev/icons?i=php' 
  },
  go: { 
    name: 'Go (Golang)', 
    skill: 45,
    color: 'bg-cyan-500',
    desc: 'Support stack used for building high-performance and concurrent services.', 
    icon: 'https://skillicons.dev/icons?i=go' 
  },
  fastapi: { 
    name: 'FastAPI', 
    skill: 55,
    color: 'bg-teal-500',
    desc: 'Library on python used for building APIs quickly and efficiently.', 
    icon: 'https://skillicons.dev/icons?i=fastapi' 
  },
  vue: { 
    name: 'Vue.js', 
    skill: 65,
    color: 'bg-emerald-500',
    desc: 'JS framework used on frontend for building interactive and dynamic user interfaces.', 
    icon: 'https://skillicons.dev/icons?i=vue' 
  },
  tailwind: { 
    name: 'Tailwind CSS', 
    skill: 60,
    color: 'bg-sky-500',
    desc: 'CSS framework for rapid UI development with utility-first approach.', 
    icon: 'https://skillicons.dev/icons?i=tailwind' 
  }
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
  <section id="stack" class="scroll-mt-24">
    <h3 class="text-2xl font-bold mb-6 flex items-center gap-3">
      <span class="w-8 h-1 bg-blue-500 rounded-full"></span> Tech Stack
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

      <div class="w-full mt-2 flex flex-col">
        <transition name="fade" mode="out-in">
          <div :key="activeTech" class="w-full">
            <div class="bg-slate-900 p-8 rounded-2xl border border-slate-700 w-full min-h-[140px] flex flex-col items-center">
              <h4 class="text-3xl font-bold text-blue-400 mb-8 text-center w-full">
                {{ techContent[activeTech].name }}
              </h4>
              <div class="flex flex-col gap-5 w-full text-left">
                <div class="flex items-center gap-4">
                  <span class="text-slate-200 text-xl font-medium w-20 shrink-0 capitalize">Skill :</span>
                  <div class="flex-grow h-4 bg-white overflow-hidden flex items-center rounded-sm">
                    <div 
                      :class="`h-full ${techContent[activeTech].color} transition-all duration-700 ease-out`" 
                      :style="`width: ${techContent[activeTech].skill}%`">
                    </div>
                  </div>
                  <span class="text-slate-200 text-lg w-12 text-right font-medium">{{ techContent[activeTech].skill }}%</span>
                </div>

                <div class="flex items-start gap-4">
                  <span class="text-slate-200 text-xl font-medium w-20 shrink-0 capitalize">Desc :</span>
                  <p class="text-slate-200 text-xl leading-relaxed w-full">
                    {{ techContent[activeTech].desc }}
                  </p>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<style scoped>
.fade-enter-active, .fade-leave-active { transition: opacity 0.3s ease; }
.fade-enter-from, .fade-leave-to { opacity: 0; }

.custom-scrollbar::-webkit-scrollbar { height: 6px; }
.custom-scrollbar::-webkit-scrollbar-track { background: #1e293b; border-radius: 10px; }
.custom-scrollbar::-webkit-scrollbar-thumb { background: #3b82f6; border-radius: 10px; }
.custom-scrollbar::-webkit-scrollbar-thumb:hover { background: #60a5fa; }
</style>