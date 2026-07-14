<template>
  <section id="info" class="flex items-center pt-2 pb-12 scroll-mt-24">
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center w-full">
      
      <div class="flex flex-col gap-2 text-center lg:text-left order-2 lg:order-1">
        <h3 class="text-3xl md:text-4xl text-blue-500 font-bold tracking-wide">
          Hello, I'm
        </h3>
        <h1 class="text-4xl md:text-5xl lg:text-7xl font-extrabold text-white leading-tight tracking-tight">
          Ravel
        </h1>
        <h2 class="text-2xl md:text-3xl font-bold text-slate-300">
          I'm a Backend Developer
        </h2>
        <p class="text-slate-400 text-base md:text-lg leading-relaxed mt-2 max-w-2xl mx-auto lg:mx-0">
          I am deeply interested in programming mostly in web development. I focus my skills on backend development and frontend development as a support skill for web applications.
        </p>
        
        <div class="mt-4 flex flex-col items-center lg:items-start text-slate-400 text-base md:text-lg leading-relaxed">
          <div class="text-left">
            <p class="font-medium text-slate-300 mb-1">Languages I use:</p>
            <ul class="space-y-1 ml-2">
              <li>- Indonesian</li>
              <li>- English</li>
            </ul>
          </div>
        </div>
        <div class="mt-6">
          <a href="#projects" class="inline-block bg-blue-600 hover:bg-blue-500 text-white font-semibold px-8 py-4 rounded-xl transition-all duration-300 hover:shadow-[0_0_20px_rgba(37,99,235,0.4)] hover:-translate-y-1">
            View My Work
          </a>
        </div>
      </div>
      
      <div class="order-1 lg:order-2 flex justify-center lg:justify-end">
        <div class="relative w-64 h-64 md:w-80 md:h-80 lg:w-[400px] lg:h-[450px]">
          <div class="absolute inset-0 bg-blue-500/20 rounded-full blur-3xl"></div>
          <img 
            src="../assets/prof.png" 
            alt="Profile" 
            class="relative w-full h-full object-cover rounded-3xl border border-slate-700/50 shadow-2xl rotate-2 hover:rotate-0 transition-transform duration-500" 
          />
        </div>
      </div>
      
    </div>
  </section>
</template>

<style scoped>
section {
  animation: fadeIn 1s ease-out forwards;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>