<script setup>
import YouTubeButton from "./YouTubeButton.vue";

const {meal} = defineProps({
  meal: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div

      class="bg-white shadow rounded-xl">
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
        <YouTubeButton :href="meal.strYoutube"></YouTubeButton>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>