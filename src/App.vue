<script setup lang="ts">
import { computed } from "vue";
import UserCard from "./components/UserCard.vue";

const userCardsCount = computed(() => {
  return Math.floor(Math.random() * 10) + 2;
});
</script>

<template>
  <div class="box-border bg-gray-100 min-h-screen h-full">
    <template v-for="i in userCardsCount" :key="i">
      <UserCard />
    </template>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
