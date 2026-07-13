<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const animatedTexts = [
  'Hi there!',
  'Welcome to my profile',
  'Glad to see you here!'
]

const displayText = ref('')
const currentIndex = ref(0)

let isDeleting = false
let charIndex = 0
let timer

const typeEffect = () => {
  const currentText = animatedTexts[currentIndex.value]

  if (isDeleting) {
    displayText.value = currentText.substring(0, charIndex - 1)
    charIndex--
  } else {
    displayText.value = currentText.substring(0, charIndex + 1)
    charIndex++
  }

  let typingSpeed = isDeleting ? 50 : 100

  if (!isDeleting && charIndex === currentText.length) {
    typingSpeed = 2000 
    isDeleting = true
  } 
  else if (isDeleting && charIndex === 0) {
    isDeleting = false
    currentIndex.value = (currentIndex.value + 1) % animatedTexts.length
    typingSpeed = 500 
  }

  timer = setTimeout(typeEffect, typingSpeed)
}

onMounted(() => {
  typeEffect()
})

onUnmounted(() => {
  clearTimeout(timer)
})
</script>

<template>
  <section id="hero" class="max-w-9xl mx-auto text-white">
    <div class="text-left w-full">
      <div class="grid w-full justify-items-start mb-2 min-h-[80px]">
        <h2 class="col-start-1 row-start-1 text-[clamp(1.75rem,5vw,3rem)] font-bold pb-2 leading-relaxed">
          <span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-teal-300">
            {{ displayText }}
          </span>
          <span class="text-teal-300 animate-pulse">|</span>
        </h2>
      </div>
    </div>
  </section>
</template>