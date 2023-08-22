<template>
  <navbar />
  <main class="bg-[#d6d3d1] min-h-[calc(100vh-64px)] h-full pb-4">
    <div class="max-w-[1200px] mx-auto">
      <router-view />
    </div>
    <p class="author fixed right-3 bottom-2 fpnt-medium z-20 text-[#364b4a] italic ">By Ernazarova Ozoda</p>
  </main>
</template>

<script setup>
import Navbar from "./Navbar.vue"
</script>

<style>
.author{
  font-family: 'Dancing Script', cursive;
}
</style>