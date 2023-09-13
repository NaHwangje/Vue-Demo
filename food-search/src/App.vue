<script setup>
import { ref } from "vue";

const food = ref(null);

fetch("https://www.themealdb.com/api/json/v1/1/random.php")
  .then((res) => res.json())
  .then((json) => {
    let data = json.meals[0];
    data.ingredients = [];
    for (let i = 1; i <= 20; i++) {
      if (data[`strIngredient${i}`]) {
        let ingredient = {
          name: data[`strIngredient${i}`],
          measure: data[`strMeasure${i}`],
        };
        data.ingredients.push(ingredient);
      } else break;
    }
    food.value = data;
  });
</script>

<template>
  <div>
    <div class="bg-white text-black shadow rounded-xl">
      <img :src="food.strMealThumb" class="rounded-t-xl" alt="" />
      <div class="text-3xl font-bold mt-4">{{ food.strMeal }}</div>
      <div v-for="i of food.ingredients" class="grid grid-cols-2">
        <div class="text-right pr-2">{{ i.name }}</div>
        <div class="text-left pl-2">{{ i.measure }}</div>
      </div>
    </div>
    <div class="p-8">
      <a
        :href="food.strYoutube"
        class="bg-blue-800 text-white px-8 py-4 font-bold hober:text-white hover:bg-black"
        >조리법 영상</a
      >
    </div>
  </div>
</template>