<script setup>
import { ref } from "vue";
import draggable from "vuedraggable";
const meals = ref([
  "Hamburger",
  "Pizza",
  "Spaghetti",
  "Tacos",
  "Teriyaki Chicken",
]);
const yuckyMeals = ref(["Bat wing soup", "Spicy Octopus"]);
</script>

<template>
  <h1>Favorite Foods</h1>
  <draggable v-model="meals" tag="ul" group="meals" item-key="id">
    <template #item="{ element: meal }">
      <li>{{ meal }}</li>
    </template>
  </draggable>

  <h1>Terrible Foods</h1>
  <draggable v-model="yuckyMeals" tag="ul" group="meals">
    <template #item="{ element: meal }">
      <li>{{ meal }}</li>
    </template>
  </draggable>
</template>

<style scoped>
html {
  font-size: 1.5rem;
}

h1 {
  margin-bottom: 0;
}
ul {
  margin-top: 0;
}
</style>
