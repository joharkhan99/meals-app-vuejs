<template>
  <div class="p-8">
    <input type="text" class="rounded border-2 border-gray-200 w-full" placeholder="Search for Meals" v-model="keyword" @change="searchMeals">
  </div>

  <div class="grid grid-cols-1 md:grid-cols-4 gap-3 p-8">
    <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">

      <router-link to="/">
        <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t-2xl h-40 w-full object-cover">
      </router-link>

      <div class="px-3">
        <h3 class="px-3 font-semibold">{{ meal.strMeal }}</h3>

        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Excepturi, eligendi ad laudantium consequatur tenetur at natus qui tempore non vero facere consectetur. Provident molestiae hic
          laboriosam id iure perspiciatis alias?
        </p>

        <div class="px-3 mt-4">
          <a :href="meal.strYoutube" target="_blank" class="px-3 py-2 rounded border-2 hover:bg-red-500 hover:text-white border-red-600">YouTube</a>
        </div>

      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import axiosClient from '../axiosClient.js';
import store from '../store';

const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch('searchMeals', keyword.value);
}

</script>