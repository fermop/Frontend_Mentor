<script setup>
  import { ref } from 'vue'
  import Footer from './components/Footer.vue'

  const email = ref(null)
  const alert = ref('')
  const error = ref(false)

  const validateForm = () => {
    // Empty input
    if (email.value === '') {
      alert.value = 'Please provide an email'
      error.value = true
      return
    }

    // Invalid email
    const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
    if (!regex.test(email.value)) {
      alert.value = 'Please provide a valid email'
      error.value = true
      return
    }

    error.value = false
    email.value = null
    alert.value = 'You are now subscribed!'

    setTimeout(() => {
      alert.value = ''
    }, 2000);

  }
</script>

<template>
  <main
    class="flex flex-col sm:flex-row"
  >
  <!-- Left part -->
   <div class="sm:w-[60%] sm:flex sm:flex-col sm:items-center sm:min-h-[100dvh]">
     <header class="w-full max-w-[28rem] p-[2rem] sm:py-[3rem] lg:px-0">
       <img src="/assets/images/logo.svg" alt="">
     </header>
     
       <div class="sm:hidden">
         <img
           src="/assets/images/hero-mobile.jpg"
           alt=""
           class="w-full"
         >
       </div>
       
       <section
         class="text-center px-[2.25rem] py-[4rem] mx-auto space-y-[1rem] sm:space-y-[2rem] max-w-[28rem] sm:text-left lg:px-0 sm:py-[5rem]"
       >
         <h1 class="text-custom-desaturated-red uppercase font-light text-[2.5rem] leading-[2.5rem] tracking-[.5rem] md:text-7xl md:leading-[4.5rem] md:tracking-[1rem]">We're <span class="text-custom-dark-grayish-red font-semibold">coming soon</span></h1>
         
         <p
           class="text-custom-desaturated-red text-[.875rem] sm:text-base"
         >Hello fellow shoppers! We're currently building our new fashion store. 
         Add your email below to stay up-to-date with announcements and our launch deals.</p>
       
         <form
           class="relative mb-2"
           novalidate
           @submit.prevent="validateForm"
         >
           <input 
             type="email"
             placeholder="Email Address"
             class="w-full text-left text-base placeholder:text-custom-desaturated-red border-1 border-custom-desaturated-red rounded-full p-[1rem] pl-6"
             :class="{'border-custom-soft-red' : error}"
             v-model="email"
           >
           
           <div
             class="absolute top-0 right-0 w-[25%] h-full flex align-center justify-end"
           >
           <img
             src="/assets/images/icon-error.svg"
             alt=""
             class="py-[1rem] mr-[1rem] md:absolute right-24"
             v-if="error"
           >
   
           <button
             class="min-w-[5rem] w-full sm:w-[6.25rem] rounded-full flex items-center justify-center bg-linear-to-r from-gradient-left to-gradient-right shadow-xl cursor-pointer hover:bg-none hover:bg-hover"
             aria-label="Submit button form"
           >
             <img
               src="/assets/images/icon-arrow.svg"
               alt=""
               class="py-[1rem]"
             >
           </button>
           </div>
         </form>
   
         <p 
           class="text-left pl-6 italic"
           :class="[alert && !error ? 'text-green-400' : 'text-custom-soft-red']"
           v-if="alert"
         >{{ alert }}</p>
       </section>

       <Footer class="hidden"/>
   </div>

    <!-- Right part -->
    <div class="hidden sm:block w-[40%] min-h-[100vh] bg-[url(/assets/images/hero-desktop.jpg)] bg-cover bg-center">
    </div>
  </main>
</template>