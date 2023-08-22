<template>
  <header class="bg-[#e7e5e4] shadow-lg h-16 flex justify-between items-strech sticky top-0 left-0 right-0 z-20">
    <router-link
      :to="{ name: 'home' }"
      class="inline-flex items-center h-full px-5 text-[#364b4a] font-bold text-lg hover:scale-105"
    >
      Home
    </router-link>
    <div class="flex items-center gap-1">
      <router-link
        :to="{ name: 'byName' }"
        class="inline-flex items-center px-2 text-[#364b4a] font-medium h-full transition-colors hover:bg-[#364b4a] hover:text-white"
      >
        Search Meals
      </router-link>
      <router-link
        :to="{ name: 'byLetter' }"
        class="inline-flex items-center px-2 text-[#364b4a] font-medium h-full transition-colors hover:bg-[#364b4a] hover:text-white"
      >
        Meals By Letter
      </router-link>
      <router-link
        :to="{ name: 'ingredients' }"
        class="inline-flex items-center px-2 text-[#364b4a] font-medium h-full transition-colors hover:bg-[#364b4a] hover:text-white"
      >
        Meals By Ingredients
      </router-link>
    </div>
  </header>
</template>

<script setup>

</script>