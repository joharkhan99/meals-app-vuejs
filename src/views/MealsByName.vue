<template>
  <div class="p-8">
    <input type="text" class="rounded border-2 border-gray-200 w-full" placeholder="Search for Meals" v-model="keyword" @change="searchMeals">
  </div>

  <div class="grid grid-cols-1 md:grid-cols-4 gap-3 p-8">
    <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">

      <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
        <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t-2xl h-40 w-full object-cover">
      </router-link>

      <div class="px-3">
        <h3 class="px-3 font-semibold">{{ meal.strMeal }}</h3>

        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Excepturi, eligendi ad laudantium consequatur tenetur at natus qui tempore non vero facere consectetur. Provident molestiae hic
          laboriosam id iure perspiciatis alias?
        </p>

        <div class="px-3 mt-4">
          <YoutubeButton :href="meal.strYoutube" />
        </div>

      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';
import axiosClient from '../axiosClient.js';
import store from '../store';
import { useRoute } from 'vue-router';
import YoutubeButton from '../components/YoutubeButton.vue';

const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch('searchMeals', keyword.value);
}

onMounted(() => {
  keyword.value = route.params.name;
  if (keyword.value) {
    searchMeals();
  }
})
</script>