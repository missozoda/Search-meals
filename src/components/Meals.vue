<template>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-6 px-8 py-3">
    <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
  </div>
  <div v-if="!meals.length" class="flex justify-center text-[#364b4a] p-8">
    There are no meals
  </div>
</template>

<script setup>
import MealItem from './MealItem.vue';

const { meals } = defineProps({
  meals: {
    required: true,
    type: Array,
  }
})

</script>