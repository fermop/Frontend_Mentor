<script setup>
  const props = defineProps({
      question: {
          type: Object,
          required: true
      }
  })

  defineEmits(['accordion-toggle'])
</script>

<template>
  <div 
    class="not-last:border-b-1 border-purple-100 cursor-pointer"
    @click="$emit('accordion-toggle', question.index)"
  >
    <div class="group flex justify-between align-center gap-[2rem] my-[1.25rem]">
      <h2 class="text-purple-950 group-hover:text-purple-400 duration-250 font-semibold text-[1.125rem]/[1.5rem]">{{ question.title }}</h2>
        <img 
          class="w-[2rem] cursor-pointer group-hover:opacity-[.7] duration-250"
          :src="[question.state ? './assets/images/icon-plus.svg' : './assets/images/icon-minus.svg']"
          alt="Toggle button"
        >
    </div>

    <p 
      :class="{ hidden: question.state }"
      class="text-normal text-purple-600 mb-[1.25rem]">{{ question.content }}</p>
  </div>
</template>