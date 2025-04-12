<script setup>
  import { ref, onMounted } from 'vue';
  import { db } from './data/questions'
  import Question from './components/Question.vue';

  const questions = ref([])

  onMounted(() => {
    questions.value = db;
  })

  const accordionToggle = (index) => {
    questions.value[index].state = !questions.value[index].state
  }

</script>

<template>

  <div>
    <img
      alt="Background pattern" 
      src="/assets/images/background-pattern-mobile.svg"
      class="desktop:hidden w-full"
    >
    <img
      alt="Background pattern" 
      src="/assets/images/background-pattern-desktop.svg"
      class="hidden desktop:block w-full"
    >
  </div>

  <main class="absolute top-0 w-[100vw] h-[100%] grid gap-1">
    <!-- Accordion -->
    <div class="bg-white w-[90%] max-w-[37.5rem] m-auto pt-[1.5rem] px-[1.25rem] pb-[1rem] md:px-[2.5rem] md:py-[2.625rem] rounded-[.75rem] shadow-xl">
      <header class="flex align-center gap-[2rem] md:mb-[2rem]">
        <img class="w-[1.5rem] md:w-[2rem]" src="/assets/images/icon-star.svg" alt="Star icon">
        <h1 class="text-purple-950 font-bold text-[2rem] md:text-5xl">FAQs</h1>
      </header>
  
      <Question
        v-for="question in questions"
        :question="question"
        @accordion-toggle="accordionToggle"
      />
    </div>
    <div class="attribution">
      Challenge by <a class="font-bold text-purple-900 hover:opacity-[.7] duration-250" href="https://www.frontendmentor.io/solutions/faq-accordion-main-AOIPWge2U2" target="_blank">Frontend Mentor</a>. 
      Coded by <a class="font-bold text-purple-900 hover:opacity-[.7] duration-250" href="https://www.frontendmentor.io/solutions/faq-accordion-main-AOIPWge2U2" target="_blank">Fernando Pérez</a>.
    </div>
  </main>


</template>