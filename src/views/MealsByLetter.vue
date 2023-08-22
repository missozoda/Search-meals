<template>
  <div class="p-8">
    <h1 class="text-4xl font-bold mb-4 text-[#364b4a]">Meals by Letter</h1>
  </div>
  <div class="flex flex-wrap justify-between gap-2 px-8 mb-6">
    <router-link
      :to="{ name: 'byLetter', params: { letter } }"
      v-for="letter of letters"
      :key="letter"
      :class="(route.params.letter === letter ? 'bg-[#616974] text-white' : 'hover:bg-[#616974] hover:text-white') + ' px-2 py-1 rounded flex items-center justify-center font-medium hover:scale-125 transition-all'"
    >
      {{ letter }}
    </router-link>
  </div>

  <Meals :meals="meals" />
</template>

<script setup>
import { computed } from "@vue/reactivity";
import { onMounted, watch } from "vue";
import { useRoute } from "vue-router";
import store from "../store";
import Meals from "../components/Meals.vue";

const route = useRoute();
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const meals = computed(() => store.state.mealsByLetter);

watch(route, () => {
  store.dispatch("searchMealsByLetter", route.params.letter);
});

onMounted(() => {
  store.dispatch("searchMealsByLetter", route.params.letter);
});
</script>