<script setup>
import { reactive } from "vue";

const data = reactive({
  food: null,
});

fetch("https://www.themealdb.com/api/json/v1/1/lookup.php?i=52772")
  .then((response) => response.json())
  .then((json) => data.food = json)
  .catch((error) => alert(error));
</script>

<template>
  <div>
    {{ data.food }}
  </div>
</template>