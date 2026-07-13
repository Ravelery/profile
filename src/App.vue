<script setup>
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import Info from './components/Info.vue'
import Stack from './components/Stack.vue'
import Tool from './components/Tool.vue'
import Projects from './components/Projects.vue'
import Contact from './components/Contact.vue'
</script>

<template>
  <div class="min-h-screen bg-slate-900 text-slate-200 font-sans selection:bg-blue-500 selection:text-white pb-10">
    <Navbar />
    <main class="max-w-5xl mx-auto px-6 pt-12 space-y-4">
      <Hero />
      <Info />
      <Stack />
      <Tool />
      <Projects />
      <Contact />
    </main>
  </div>
</template>