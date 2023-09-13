<script setup>
import { ref } from "vue";

const food = ref(null);


fetch('https://www.themealdb.com/api/json/v1/1/random.php')
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
    <div>{{ food }}</div>
    <div class="bg-white text-black shadow rounded-xl">
      <img :src="food.strMealThumb" class="rounded-t-xl" alt="" />
      <div>{{ food.strMeal }}</div>
      <div v-for="i of food.ingredients">
        <div>{{ i.name }}</div>
        <div>{{ i.measure }}</div>
        <!-- 수정 -->
      </div>
    </div>
  </div>
</template>