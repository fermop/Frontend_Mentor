<script setup>
  import { ref } from 'vue'
  import RateCard from './components/RateCard.vue'
  import Footer from './components/Footer.vue'

  const buttonsState = ref({
    button_01: false,
    button_02: false,
    button_03: false,
    button_04: false,
    button_05: false
  })

  const buttonSelected = ref(0)
  const error = ref(false)
  const rated = ref(false)
  const loading = ref(false)

  const selectButton = (button) => {
    error.value = false

    if (buttonsState.value[`button_0${button}`]) {
      buttonsState.value[`button_0${button}`] = false
      return
    }

    buttonsState.value.button_01 = false
    buttonsState.value.button_02 = false
    buttonsState.value.button_03 = false
    buttonsState.value.button_04 = false
    buttonsState.value.button_05 = false

    buttonsState.value[`button_0${button}`] = true
    buttonSelected.value = button
  }

  const submitForm = () => {
    if (!Object.values(buttonsState.value).includes(true)) {
      error.value = true
      return
    }

    loading.value = true

    setTimeout(() => {
      loading.value = false
    }, 1000);

    rated.value = buttonSelected.value
  }
</script>

<template>
  <main class="h-[100vh] flex flex-col items-center justify-center gap-12">
    <RateCard
      :buttonsState="buttonsState"
      :error="error"
      :loading="loading"
      :rated="rated"
      @select-button="selectButton"
      @submit-form="submitForm"
    />

    <Footer
    />
  </main>
</template>