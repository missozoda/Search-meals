<template>
  <div class="p-8">
    <input 
    type="text"
    v-model="keyword" 
    class="rounded border-2 border-gray-200 w-full" placeholder="Search for Melas"
    @change="searchmeals">
  </div>

  <div class="grid grid-cols-1 md:grid-cols-3 gap-1">
    <div v-for="meal of meals" :key="meal.idMeal">
      <img :src="meal.strMealThumb" :alt="meal.strMeal">
      <h3 class="">{{ meal.strmeal }}</h3>
      <div>
        <a :href="meal.strYoutube" target="_blank">Youtube</a>
        <router-link to="/">View</router-link>
      </div>
    </div>
  </div>
</template>

<script setup>
import store from '../store';
import { computed, ref } from 'vue';


  const keyword = ref(""); 
  const meals = computed(() => store.state.searchedMeals)

  function searchmeals() {
    store.dispatch('searchMeals', keyword.value)
  }

</script>