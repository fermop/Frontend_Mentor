<script setup>
  import { computed, ref } from 'vue';
  import Socials from './components/Socials.vue';
  import Footer from './components/Footer.vue';

  const email = ref('')
  const alert = ref(false)
  const errorMsg = ref('')
  const success = ref(false)

  const validateEmail = (value) => {
    // Empty input
    if (value === '') {
      alert.value = true
      errorMsg.value = 'Please provide an email address';
      return 
    }
    // Validate email address
    const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
    if (!regex.test(value)) {
      alert.value = true
      errorMsg.value = 'Please provide a valid email address';
      return
    }

    // Success
    errorMsg.value = ''
    alert.value = true
    success.value = true;
    email.value = ''
  }

  const sendEmail = () => {
    validateEmail(email.value)
    setTimeout(() => {
      alert.value = false
      errorMsg.value = ''
      success.value = false
    }, 3000)
  }

  const hasError = computed(() => {
    return errorMsg.value
  })
</script>

<template>

  <div
    class="w-[90%] m-auto max-w-[40rem]"
  >
    <header
      class="flex justify-center mt-[5rem] mb-[2.5rem]"
    >
      <img src="/assets/images/logo.svg" alt="Logo">
    </header>

    <h1
      class="text-neutral-gray text-center text-xl sm:text-5xl"
    >We are launching <span class="text-neutral-very-dark-blue font-bold">soon!</span></h1>

    <p
      class="text-center text-base sm:text-xl text-neutral-very-dark-blue mt-[2rem] mb-[3rem]"
    >Subscribe and get notified</p>
    
    <form 
      class="grid gap-[1rem] sm:grid-cols-3 px-[2rem] sm:px-0"
      @submit.prevent="sendEmail"
      novalidate
    >
      <div class=" sm:col-span-2">
        <input 
          type="email"
          class="w-full border-1 rounded-full p-[1rem] pl-[3rem]"
          :class="[hasError ? 'border-secondary-light-red' : 'border-secondary-pale-blue']"
          placeholder="Your email address"
          v-model="email"
        >
  
        <!-- Alert -->
        <div
          v-if="alert"
          class="text-center sm:text-left sm:pl-[3rem] italic mt-[.5rem] mb-[1rem] text-sm"
        >
          <p 
            class="text-secondary-light-red"
            v-if="hasError"
          >{{ errorMsg }}</p>
          
          <p 
            class="text-green-400"
            v-if="success">Welcome! You are now subscribed!</p>
        </div>
      </div>

      <button
        class="max-h-[3.5rem] bg-primary-blue text-white font-bold w-full rounded-full p-[1rem] shadow-xl shadow-secondary-pale-blue cursor-pointer hover:opacity-70 duration-250"
      >Notify Me</button>
    </form>

    <img 
      class="mt-[5rem] mb-[7.5rem]"
      src="/assets/images/illustration-dashboard.png" 
      alt="Illustration dashboard"
      >
    
    <Socials />

    <section>
      <p class="text-center my-[3rem] text-sm text-neutral-gray">&copy; Copyright Ping. All rights reserved.</p>
    </section>
  </div>
  
  <Footer class="hidden"/>
</template>