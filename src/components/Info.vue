<script setup>
import { ref } from 'vue'

const activeInfo = ref('about')

const infoContent = {
  about: "<strong>Who am I?</strong><br><br>I am a student at SMK Negeri 1 Sukawati who deeply interested in programming. i'm focused my skills on backend development and do data analysis as my secondary skill.",
  education: "<strong>Education</strong><br><br>• SMK Negeri 1 Sukawati. (Software Engineering)<br>(2024 - present)<br>• SMP Negeri 3 Pupuan. <br>(2021 - 2024)",
  language: "<strong>Language</strong><br><br>• Indonesian<br>• English"
}
</script>

<template>
  <section id="info" class="scroll-mt-24">
    <div class="flex flex-col md:flex-row gap-6">

      <div class="w-full md:w-5/12 lg:w-1/3 p-6 rounded-3xl border border-sky-700/50 flex flex-row md:flex-col items-center md:items-start gap-6 bg-slate-800">
        <img src="../assets/profile.jpg" alt="Profile" class="w-24 h-24 md:w-32 md:h-32 rounded-2xl border-4 border-sky-700 object-cover shrink-0" />
        <div>
          <h2 class="text-2xl font-bold text-white mb-2">I Made Dwik Prawira</h2>
          <h3 class="text-blue-500 font-medium text-sm md:text-base uppercase tracking-wide">• Backend Dev</h3>
        </div>
      </div>

      <div class="w-full md:w-7/12 lg:w-2/3 flex flex-row md:flex-col gap-4 md:gap-6">

        <div class="flex flex-col md:flex-row gap-3 w-1/3 md:w-full shrink-0">
          <button 
            @click="activeInfo = 'about'" 
            :class="activeInfo === 'about' ? 'bg-blue-600 text-white border-blue-500' : 'bg-slate-800 text-slate-400 border-slate-700'" 
            class="px-4 py-2.5 text-sm md:text-lg rounded-xl border transition-all text-center md:text-left hover:bg-slate-700">
            About Me
          </button>
          <button 
            @click="activeInfo = 'education'" 
            :class="activeInfo === 'education' ? 'bg-blue-600 text-white border-blue-500' : 'bg-slate-800 text-slate-400 border-slate-700'" 
            class="px-4 py-2.5 text-sm md:text-lg rounded-xl border transition-all text-center md:text-left hover:bg-slate-700">
            Education
          </button>
          <button 
            @click="activeInfo = 'language'" 
            :class="activeInfo === 'language' ? 'bg-blue-600 text-white border-blue-500' : 'bg-slate-800 text-slate-400 border-slate-700'" 
            class="px-4 py-2.5 text-sm md:text-lg rounded-xl border transition-all text-center md:text-left hover:bg-slate-700">
            Language
          </button>
        </div>

        <div class="w-2/3 md:w-full bg-slate-800/50 border border-slate-700/50 p-5 md:p-6 rounded-2xl min-h-[160px]">
          <transition name="fade" mode="out-in">
            <div :key="activeInfo" class="text-sm md:text-base text-slate-300 leading-relaxed" v-html="infoContent[activeInfo]"></div>
          </transition>
        </div>

      </div>

    </div>
  </section>
</template>

<style scoped>
.fade-enter-active, .fade-leave-active { 
  transition: opacity 0.3s ease, transform 0.3s ease; 
}
.fade-enter-from, .fade-leave-to { 
  opacity: 0; 
  transform: translateY(10px); 
}
</style>