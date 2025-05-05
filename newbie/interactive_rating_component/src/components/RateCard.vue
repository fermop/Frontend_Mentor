<script setup>
  import Spinner from "./Spinner.vue";

  defineProps({
    buttonsState: {
      type: Object,
      required: true
    },
    error: {
      type: Boolean,
      required: true
    },
    loading: {
      type: Boolean,
      required: true
    },
    rated: {
      type: [Boolean, Number],
      required: true
    }
  })

  defineEmits(['select-button', 'submit-form'])
</script>

<template>
  <div
    class="w-[87%] max-w-[25.75rem] min-h-[22.5rem] mx-auto bg-custom-Grey-900 p-[1rem] sm:p-[2rem] rounded-[.75rem] sm:rounded-[1.25rem] flex flex-col items-center justify-center"
  >
    <form 
      v-if="rated === false"
      class=" space-y-[1.25rem]"
      @submit.prevent="$emit('submit-form')"
    >
      <img
        src="/assets/images/icon-star.svg"
        alt=""
        class="bg-gray-700 p-[.75rem] rounded-full"
      >
  
      <h1
        class="text-custom-White font-bold text-2xl sm:text-3xl"
      >How did we do?</h1>
  
      <p
        class="text-custom-Grey-500 text-[.9063rem] sm:text-[.9375rem]"
      >Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!</p>
  
      
      <div class="flex justify-between text-custom-Grey-500 text-[.875rem] text-center leading-11 sm:leading-13">
        <button
          type="button"
          class="cursor-pointer w-10 h-10 sm:w-13 sm:h-13 rounded-full hover:bg-custom-White hover:text-custom-Grey-950 duration-250"
          :class="[buttonsState.button_01 ? 'bg-custom-Orange-500 text-custom-Grey-950' : 'bg-gray-700']"
          @click="$emit('select-button', 1)"
        >
          1
        </button>
        <button
          type="button"
          class="cursor-pointer w-10 h-10 sm:w-13 sm:h-13 rounded-full hover:bg-custom-White hover:text-custom-Grey-950 duration-250"
          :class="[buttonsState.button_02 ? 'bg-custom-Orange-500 text-custom-Grey-950' : 'bg-gray-700']"
          @click="$emit('select-button', 2)"
        >
          2
        </button>
        <button
          type="button"
          class="cursor-pointer w-10 h-10 sm:w-13 sm:h-13 rounded-full hover:bg-custom-White hover:text-custom-Grey-950 duration-250"
          :class="[buttonsState.button_03 ? 'bg-custom-Orange-500 text-custom-Grey-950' : 'bg-gray-700']"
          @click="$emit('select-button', 3)"
        >
          3
        </button>
        <button
          type="button"
          class="cursor-pointer w-10 h-10 sm:w-13 sm:h-13 rounded-full hover:bg-custom-White hover:text-custom-Grey-950 duration-250"
          :class="[buttonsState.button_04 ? 'bg-custom-Orange-500 text-custom-Grey-950' : 'bg-gray-700']"
          @click="$emit('select-button', 4)"
        >
          4
        </button>
        <button
          type="button"
          class="cursor-pointer w-10 h-10 sm:w-13 sm:h-13 rounded-full hover:bg-custom-White hover:text-custom-Grey-950 duration-250"
          :class="[buttonsState.button_05 ? 'bg-custom-Orange-500 text-custom-Grey-950' : 'bg-gray-700']"
          @click="$emit('select-button', 5)"
        >
          5
        </button>
      </div>
  
      <p 
        class="text-custom-Orange-500 text-xs font-semibold italic"
        v-if="error"
      >You have to select one option!</p>
  
      <button
        type="submit"
        class="cursor-pointer w-full text-center bg-custom-Orange-500 rounded-full py-3 uppercase font-semibold tracking-widest text-[15px] hover:bg-custom-White duration-250"
      >Submit</button>
    </form>

    <Spinner
      v-if="loading"
    />

    <div
      class="flex flex-col items-center gap-[1rem] text-center py-[1rem]"
      v-if="!loading && rated"
    >
      <img
        src="/assets/images/illustration-thank-you.svg"
        alt=""
      >

      <p class="bg-custom-Grey-900 text-custom-Orange-500 font-normal text-sm p-[.5rem] px-[1rem] rounded-full">You selected {{ rated }} out of 5</p>

      <h2 class="text-custom-White text-2xl">Thank you!</h2>

      <p class="text-custom-Grey-500 text-[15px]">We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in touch!</p>
    </div>
  </div>
</template>