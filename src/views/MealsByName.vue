<script setup>
import {computed, onMounted, ref} from "vue";
import store from "../store/index.js";
import {useRoute} from "vue-router";
import MealDetails from "./MealDetails.vue";
import YouTubeButton from "../components/YouTubeButton.vue";


const route = useRoute()
const keyword = ref('');
const meals = computed(()=> store.state.searchedMeals);

function searchMeals(){
  store.dispatch('searchMeals', keyword.value);
  console.log(meals.value)
}

onMounted(()=>{
 keyword.value = route.params.name;
 if(keyword.value){
   searchMeals();
 }
})
</script>

<template>
<div class="p-8 pb-0">
  <input
      type="text" name="" id=""
      v-model="keyword"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Search for meals"
      @change="searchMeals"
  />
</div>

  <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
    <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">
      <router-link :to="{name: 'mealDetails', params: {id: meal.idMeal}}">
        <img
            :src="meal.strMealThumb"
            :alt="`${meal.strMeal} image`"
            class="rounded-t-xl w-full h-48 object-cover"
        />
      </router-link>
      <div class="px-3">
        <h3 class=" font-bold">{{meal.strMeal}}</h3>
        <p class="mb-4">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Culpa cum doloribus iste.</p>
        <div class="flex items-center justify-between pb-4">
          <YouTubeButton :href="meal.strYoutube"/>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>