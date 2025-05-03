<script setup>
  import { ref } from 'vue';
  import Form from './components/Form.vue';
  import Modal from './components/Modal.vue';
  import Footer from './components/Footer.vue';

const formValues = ref({
  first_name: '',
  last_name: '',
  email: '',
  password: ''
})

const error = ref(false)
const invalidEmail = ref(false)

const isOpen = ref(false)

function closeModal() {
  isOpen.value = false
}

function openModal() {
  isOpen.value = true
}

const validateForm = () => {
  error.value = false
  invalidEmail.value = false

  // Empty form fields and email
  if (Object.values(formValues.value).includes('')) {
    error.value = true
  }

  // Validate email
  const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
  if (!regex.test(formValues.value.email)) {
    error.value = true
    invalidEmail.value = true
  }

  if (error.value) {
    return
  }

  // Valid form
  Object.assign(formValues.value, {
    first_name: '',
    last_name: '',
    email: '',
    password: ''
  })

  // Open Modal
  openModal()
}
</script>

<template>
  <main class="max-w-[69.375rem] mt-[6rem] mb-[5rem] w-[87%] xl:w-[100%] m-auto flex flex-col gap-[4rem] lg:flex-row lg:justify-between xl:m-0">
    <header class="lg:w-[50%] text-center lg:text-left space-y-[1rem] md:flex md:flex-col justify-center">
      <h1 class="text-white font-bold text-[1.6875rem] px-[1rem] lg:px-0 lg:text-[3rem]">Learn to code by watching others</h1>
      <p class="text-base text-white">See how experienced developers solve problems in real-time. Watching scripted tutorials is great, but understanding how developers think is invaluable.</p>
    </header>

    <section class="space-y-[1.5rem]">
      <header class="bg-custom-Blue text-custom-Grayish-Blue text-center rounded-lg px-[3rem] py-[1rem] shadow-[0_8px_0px_0px_rgba(0,0,0,0.25)]">
          <h2 class="sr-only">Advertisement</h2>
          <span class="font-bold text-white ">Try it free 7 days </span>then $20/mo. thereafter
      </header>

      <Form 
        :formValues="formValues"
        :error="error"
        :invalidEmail="invalidEmail"
        @validate-form="validateForm"
      />

      <Modal 
        :isOpen="isOpen"
        @close-modal="closeModal"
      />
    </section>
  </main>

  <Footer class="my-[2rem]"/>
</template>