<script setup>
import {computed, onMounted, ref} from "vue";
import store from "../store/index.js";
import axiosClient from "../axiosClient.js";

const meals = computed(()=> store.state.meals);
const ingredients = ref([])

onMounted(async ()=>{
 const response =  await axiosClient.get('/list.php?i=list')
  console.log(response.data);
 ingredients.value = response.data;
})
</script>
<template>
  <div class="flex flex-col p-8">



  </div>
</template>
<style>

</style>