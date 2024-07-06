<script setup>
import NavBar from "./NavBar.vue";
</script>

<template>
  <nav-bar/>
  <main>
    <div class="max-w-[1200px] mx-auto">
      <router-view/>
    </div>
  </main>
</template>

<style scoped>

</style>