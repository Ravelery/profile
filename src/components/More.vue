<script setup>
import { ref } from 'vue'

const educations = ref([
  {
    id: 1,
    school: 'SMK Negeri 1 Sukawati',
    major: 'Software Engineering',
    date: '2024 - Present',
  },
  {
    id: 2,
    school: 'SMP Negeri 3 Pupuan',
    date: '2021 - 2024',
  },
])
</script>

<template>
  <section id="milestones" class="w-full bg-indigo-900/50 rounded-2xl py-16 scroll-mt-24">
    <div class="max-w-5xl mx-auto px-6">
      <div class="text-center mb-16">
        <h2 class="text-xl md:text-2xl font-bold text-white tracking-wide">
          Education & Achievements
        </h2>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12 lg:gap-24">
        
        <div>
          <h3 class="text-2xl font-bold text-cyan-400 mb-8">Education</h3>
          <div class="border-l-[3px] border-slate-700 ml-3 space-y-8">
            <div v-for="edu in educations" :key="edu.id" class="relative pl-8">
              <div class="absolute w-4 h-4 bg-cyan-400 rounded-full -left-[9.5px] top-1.5 shadow-[0_0_10px_rgba(34,211,238,0.5)]"></div>
              <h4 class="text-xl font-bold text-white">{{ edu.school }}</h4>
              <p class="text-slate-300 mt-1">{{ edu.major }}</p>
              <p class="text-teal-600/80 text-sm mt-1 font-medium">
                {{ edu.date }}
              </p>
            </div>
          </div>
        </div>

        <div>
          <h3 class="text-2xl font-bold text-cyan-400 mb-8">Certificates</h3>
          <div class="border-l-[3px] border-slate-700 ml-3 mb-10 relative">
            <div class="absolute w-4 h-4 bg-cyan-400 rounded-full -left-[9.5px] top-1.5 shadow-[0_0_10px_rgba(34,211,238,0.5)]"></div>
            <div class="pl-8 relative pb-2">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-teal-400 mb-2" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
              </svg>
              <h4 class="text-xl font-bold text-white leading-tight">Sertifikat Lomba SemiFinal Cerdas Cermat IT</h4>
              <p class="text-slate-400 text-sm mt-1 mb-2">Tingkat Nasional</p>
              <p class="text-slate-400 text-sm leading-relaxed">
                Peserta semifinal Lomba Cerdas Cermat IT tingkat nasional dalam acara SITEFEST 4.0 oleh BEM Primakara University.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>