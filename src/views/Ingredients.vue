<template>
  <div class="p-8">
    <h1 class="text-4xl font-bold mb-4">Ingredients</h1>

    <input type="text" class="rounded border-2 border-gray-200 w-full" placeholder="Search for Ingredients" v-model="keyword">

    <router-link :to="{ name: 'byIngredient', params: { ingredient: ingredient.strIngredient } }" v-for="ingredient of computedIngredients" :key="ingredient.idIngredient"
      class="bg-white rounded p-3 mb-3 shadow block">

      <h3 class="text-2xl font-bold mb-2">{{ ingredient.strIngredient }}</h3>

      <p>{{ ingredient.strDescription }}</p>
    </router-link>

  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';
import axiosClient from '../axiosClient.js';

const keyword = ref('');
const ingredients = ref([]);

// filter on input search
const computedIngredients = computed(() => {
  if (!computedIngredients) {
    return ingredients;
  }

  return ingredients.value.filter(i =>
    i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
  )
});

onMounted(() => {
  axiosClient.get('list.php?i=list')
    .then(({ data }) => {
      ingredients.value = data.meals
    })
});
</script>