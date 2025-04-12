<script setup>
  import Card from './Card.vue';
</script>

<template>
  <main 
    class="mt-8"
  >
    <header>
      <h1 
        class="text-neutral-700 font-bold text-3xl text-center"
      >Extensions List</h1>

      <div
        class="flex w-fit mt-4 mb-8 m-auto gap-4"
      >
        <p class="bg-neutral-0 py-[.25rem] text-lg px-4 border-1 rounded-full border-red-400 bg-red-400 text-neutral-0 ">All</p>
        <p class="bg-neutral-0 py-[.25rem] text-lg px-4 border-1 rounded-full border-neutral-300">Active</p>
        <p class="bg-neutral-0 py-[.25rem] text-lg px-4 border-1 rounded-full border-neutral-300">Inactive</p>
      </div>
    </header>

    <div 
      class="flex flex-wrap gap-4"
    >
      <Card/>
    </div>
  </main>
</template>