<script setup>
  const props = defineProps({
    card: {
      type: Object,
      required: true
    }
  })

  defineEmits(['remove-card'])
</script>

<template>
  <div
    class="h-[12.5rem] bg-neutral-0 dark:bg-neutral-800 p-4 rounded-[1.25rem] border-1 border-neutral-300 dark:border-neutral-600 shadow-xs flex flex-col justify-between"
  >
    <div
      class="flex gap-[1.25rem] items-start mb-[1.5rem]"
    >
      <img 
        :src="card.logo"
        :alt="card.name + ' logo'"
      >

      <div>
        <h2 class="text-xl text-neutral-900 dark:text-neutral-0 font-bold mb-1">{{ card.name }}</h2>
        <p class="text-base text-neutral-500 dark:text-neutral-400">{{ card.description }}</p>
      </div>
    </div>

    <div class="flex justify-between">
      <button
        class="text-neutral-900 dark:text-neutral-100 font-medium px-4 py-1 rounded-full border-1 border-neutral-300 dark:border-neutral-600 cursor-pointer hover:bg-red-500 hover:text-neutral-0 dark:hover:text-neutral-900 duration-250 focus:outline-offset-2 focus:outline-red-500"
        @click="$emit('remove-card', card)"
      >
        Remove
      </button>

      <label class="inline-flex items-center cursor-pointer">
        <input type="checkbox" value="" class="sr-only peer">
        <div class="relative w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-300 dark:peer-focus:ring-blue-800 rounded-full peer dark:bg-gray-700 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-red-500 dark:peer-checked:bg-red-500"></div>
      </label>
    </div>
  </div>
</template>