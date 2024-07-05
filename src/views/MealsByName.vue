<script setup>
import {computed, onMounted, ref} from "vue";
import store from "../store/index.js";
import {useRoute} from "vue-router";
import Meals from "../components/Meals.vue";


const route = useRoute()
const keyword = ref('');
const meals = computed(()=> store.state.searchedMeals);

function searchMeals(){
  store.dispatch('searchMeals', keyword.value);
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
      class="rounded border-2 border-gray-200 w-full bg-white"
      placeholder="Search for meals"
      @change="searchMeals"
  />
</div>

  <Meals :meals="meals"/>
</template>

<style scoped>

</style>