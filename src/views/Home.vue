<script setup>
import {computed} from "vue";
import store from "../store/index.js";

const meals = computed(()=> store.state.meals)
</script>
<template>
  <pre>{{meals}}</pre>
</template>
<style>

</style>