<template>
  <div class="bg-white shadow rounded-xl">

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
</template>

<script setup>
import { defineProps } from 'vue';
import YoutubeButton from './YoutubeButton.vue';

const { meal } = defineProps({
  meal: {
    required: true,
    type: Object
  }
})
</script>