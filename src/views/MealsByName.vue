<template>
  <div class="p-8 pb-0">
    <h1 class="text-4xl font-bold mb-4 text-[#364b4a]">Search Meals by Name</h1>
  </div>
  <div class="px-8 py-3 flex items-center justify-between">
    <input
      type="text"
      v-model="keyword"
      class="rounded border-2 bg-white border-gray-200 focus:ring-[#364b4a] focus:border-[#364b4a] w-full"
      placeholder="Search for Meals"
      @change="searchMeals"
    />
    <button class="px-4 py-2 ml-4 border-2 border-[#364b4a] bg-[#364b4a] hover:bg-transparent text-white hover:text-[#364b4a] rounded font-medium"
    @click="searchMeals"
    >Search</button>
  </div>
  <Meals :meals="meals" />
</template>

<script setup>
import { computed } from "@vue/reactivity";
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import store from "../store";
import Meals from '../components/Meals.vue'

const route = useRoute();
const keyword = ref("");
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  if (keyword.value) {
    store.dispatch("searchMeals", keyword.value);
  } else {
    store.commit("setSearchedMeals", []);
  }
}

onMounted(() => {
  keyword.value = route.params.name
  if (keyword.value) {
    searchMeals()
  }
})
</script>