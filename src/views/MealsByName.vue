<script setup>
import {computed, ref} from "vue";
import store from "../store/index.js";

const keyword = ref('');
const meals = computed(()=> store.state.searchedMeals);

function searchMeals(){
  store.dispatch('searchMeals', keyword.value);
}
</script>

<template>
<div class="p-8">
  <input
      type="text" name="" id=""
      v-model="keyword"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Search for meals"
      @change="searchMeals"
  />
</div>

  <div>
    <pre>{{meals}}</pre>
  </div>
</template>

<style scoped>

</style>