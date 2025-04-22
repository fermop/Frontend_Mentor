<script setup>
  import { ref, onMounted } from 'vue'

  const advice = ref('')
  const adviceId = ref('')

  onMounted(() => {
    getAdvice()
  })

  const getAdvice = async () => {
    try {
      const res = await fetch('https://api.adviceslip.com/advice')
      const data = await res.json()
      advice.value = data.slip.advice
      adviceId.value = data.slip.id
    } catch (error) {
      advice.value = 'Ups! we couldn\'t load the quote.'
      console.error(error)
    }
  }
</script>

<template>
  <div class="w-[90%] max-w-[33.75rem] bg-blue-900 text-center rounded-[.5rem] md:rounded-[1rem] px-[1rem] md:px-[3rem]">
    <h1 class="text-green-300 tracking-[8px] text-[.75rem] py-[3rem]">ADVICE #{{ adviceId }}</h1>
    <p class="text-blue-200 text-[1.75rem] font-extrabold">"{{ advice }}"</p>

    <div class="mt-[2rem] mb-[4rem] md:mt-[3rem] md:mb-[5rem]">
      <img 
        class="w-full md:hidden"
        src="/assets/images/pattern-divider-mobile.svg" alt=""
      >
      <img 
        class="w-full hidden md:block"
        src="/assets/images/pattern-divider-desktop.svg" alt=""
      >
    </div>

  </div>
  <button 
    class="bg-green-300 p-[1.25rem] rounded-full -mt-[2rem] cursor-pointer hover:shadow-[0_0_2rem] shadow-green-300 duration-250"
    @click="getAdvice"
  >
    <img src="/assets/images/icon-dice.svg" alt="">
  </button>
</template>