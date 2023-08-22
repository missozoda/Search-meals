<template>
  <div class="p-8 pb-0">
    <h1 class="text-4xl font-bold mb-4 text-[#364b4a]">Ingredients</h1>
  </div>
  <div class="px-8">
      <input
        type="text"
        v-model="keyword"
        class="my-3 rounded border-2 bg-white border-gray-200 focus:ring-[#364b4a] focus:border-[#364b4a] w-full"
        placeholder="Search for Ingredients"
      />
    <div class="grid grid-cols-1 md:grid-cols-2 gap-2 md:gap-3 mt-4">
      <a href="#"
        @click.prevent="openIngredient(ingredient)"
        v-for="ingredient of computedIngredients"
        :key="ingredient.idIngredient"
        class="block bg-[#e6e5e0] border-b border-[#364b4a] rounded p-3 mb-1 md:mb-3 shadow-md"
      >
        <h3 class="text-2xl font-bold mb-2">{{ ingredient.strIngredient }}</h3>
      </a>
    </div>
  </div>
</template>

<script setup>
import { onMounted, computed, ref } from "vue";
import { useRouter } from "vue-router";
import axiosClient from "../axiosClient";
import store from "../store";

const router = useRouter();
const keyword = ref("");
const ingredients = ref([]);
const computedIngredients = computed(() => {
  if (!computedIngredients) return ingredients;
  return ingredients.value.filter((i) =>
    i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
  );
});

function openIngredient(ingredient) {
  store.commit('setIngredient', ingredient)
  router.push({
    name: "byIngredient",
    params: { ingredient: ingredient.strIngredient },
  });
}

onMounted(() => {
  axiosClient.get("list.php?i=list").then(({ data }) => {
    ingredients.value = data.meals;
  });
});
</script>