<script setup>
  defineProps({
    formValues: {
      type: Object,
      required: true
    },
    error: {
      type: Boolean,
      required: true
    },
    invalidEmail: {
      type: Boolean,
      required: true
    },
  })

  defineEmits(['validate-form'])
</script>

<template>
  <div class="bg-white rounded-lg p-8 shadow-[0_8px_0px_0px_rgba(0,0,0,0.25)]">
    <form 
      class="grid gap-4"
      novalidate
      @submit.prevent="$emit('validate-form')"
    >
      <div>
        <div class="relative">
          <input 
            class="w-full placeholder:font-bold border-1 border-custom-Grayish-Blue rounded p-4"
            :class="[!formValues.first_name && error ? 'border-custom-Red text-custom-Red' : '']"
            type="text"
            placeholder="First Name"
            name="first-name"
            v-model="formValues.first_name"
          >
          <img 
            v-if="!formValues.first_name && error" 
            class="absolute top-4 right-6" src="/assets/images/icon-error.svg" 
            alt=""
          >
        </div>
          <p 
            class="text-custom-Red mt-1 italic text-right text-xs"
            v-if="!formValues.first_name && error"
          >First Name cannot be empty</p>
      </div>

      <div>
        <div class="relative">
          <input 
            class="w-full placeholder:font-bold border-1 border-custom-Grayish-Blue rounded p-4"
            :class="[!formValues.last_name && error ? 'border-custom-Red text-custom-Red' : '']"
            type="email"
            placeholder="Last Name"
            name="last-name"
            v-model="formValues.last_name"
          >
          <img 
            v-if="!formValues.last_name && error" 
            class="absolute top-4 right-6" src="/assets/images/icon-error.svg" 
            alt=""
          >
        </div>
        <p 
          class="text-custom-Red mt-1 italic text-right text-xs"
          v-if="!formValues.last_name && error"
        >Last Name cannot be empty</p>
      </div>

      <div>
        <div class="relative">
          <input 
            class="w-full placeholder:font-bold border-1 border-custom-Grayish-Blue rounded p-4"
            :class="[error && invalidEmail ? 'border-custom-Red text-custom-Red' : '']"
            type="text"
            placeholder="Email Address"
            name="email"
            v-model="formValues.email"
          >
          <img 
            v-if="error && invalidEmail" 
            class="absolute top-4 right-6" src="/assets/images/icon-error.svg" 
            alt=""
          >
        </div>
        <p 
          class="text-custom-Red mt-1 italic text-right text-xs"
          v-if="error && invalidEmail"
        >Looks like this is not an email</p>
      </div>

      <div>
        <div class="relative">
          <input 
            class="w-full placeholder:font-bold border-1 border-custom-Grayish-Blue rounded p-4"
            :class="[!formValues.password && error ? 'border-custom-Red text-custom-Red' : '']"
            type="password"
            placeholder="Password"
            name="password"
            v-model="formValues.password"
          >
          <img 
            v-if="!formValues.password && error" 
            class="absolute top-4 right-6" src="/assets/images/icon-error.svg" 
            alt=""
          >
        </div>
        <p 
          class="text-custom-Red mt-1 italic text-right text-xs"
          v-if="!formValues.password && error"
        >Password cannot be empty</p>
      </div>

      <button
        class="bg-custom-Green rounded uppercase text-white py-4 cursor-pointer hover:opacity-75 duration-250"
      >Claim your free trial</button>

      <p class="text-center text-custom-Grayish-Blue text-[10px] px-6">By clicking the button, you are agreeing to our <span class="font-bold text-custom-Red"><a href="#" class="hover:opacity-75 duration-250">Terms and Services</a></span></p>
    </form>
  </div>
</template>