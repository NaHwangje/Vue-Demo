<script setup>
import { reactive } from "vue";

const data = reactive({
  food: null,
});

fetch("https://www.themealdb.com/api/json/v1/1/random.php")
  .then((response) => response.json())
  .then((json) => (data.food = json.meals[0]))
  .catch((error) => console.log(error));
</script>

<template>
  <div>
    <div class="shadow bg-gray-100 text-black rounded-lg">
      <img class="rounded-t-lg" :src="data.food.strMealThumb" alt="" />
      <div>{{ data.food.strMeal }}</div>
    </div>
  </div>
</template>