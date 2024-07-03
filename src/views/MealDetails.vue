<script setup>
import {onMounted, ref} from "vue";
import {useRoute} from "vue-router";
import axiosClient from "../axiosClient.js";
import YouTubeButton from "../components/YouTubeButton.vue";

const route = useRoute();
const meal = ref({});

onMounted(()=>{
  axiosClient.get(`lookup.php?i=${route.params.id}`)
      .then(({data})=>{
        meal.value = data.meals[0] || {};
  })
})
</script>

<template>
  <div class="w-[800px] mx-auto p-8">
    <h1 class="text-5xl font-bold mb-5">{{meal.strMeal}}</h1>
    <img :src="meal.strMealThumb" :alt="`${meal.strMeal} image`">

    <div class="grid grid-cols-1 sm:grid-cols-3 text-lg py-2">
      <span><strong>Category:</strong> {{meal.strCategory}}</span>
      <span><strong>Area:</strong> {{meal.strArea}}</span>
      <span><strong>Tags:</strong> {{meal.strTags}}</span>
    </div>

    <div class="my-3">
      {{meal.strInstructions}}
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2">
      <div>
        <h2 class="text-2xl font-semibold mb-2">Ingredients</h2>
        <ul>
          <template v-for="(el, index) of new Array(20)">
            <li v-if="meal[`strIngredient${index+1}`]">
              {{index+1}}. {{meal[`strIngredient${index+1}`]}}
            </li>
          </template>
        </ul>
      </div>
      <div>
        <h2 class="text-2xl font-semibold mb-2">Measures</h2>
        <ul>
          <template v-for="(el, index) of new Array(20)">
            <li v-if="meal[`strMeasure${index+1}`]">
              {{index+1}}. {{meal[`strMeasure${index+1}`]}}
            </li>
          </template>
        </ul>
      </div>

      <div class="mt-4">
        <YouTubeButton :href="meal.strYoutube">Go to YouTube</YouTubeButton>
        <a :href="meal.strSource" target="_blank"
           class="ml-3 px-3 py-2 border-2 border-transparent rounded text-indigo-600 hover:bg-indigo-600 hover:text-white transition-colors"
        >
          View Original Source
        </a>
      </div>
    </div>

  </div>
</template>

<style scoped>

</style>