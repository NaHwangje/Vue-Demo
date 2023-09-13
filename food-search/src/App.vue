<script setup>
let foods = [
  10, 3, 4, 17, 8
]
foods= foods.map(x=> x*2)
</script>

<template>
  <div class="text-2xl">
    <div v-for="food of foods">{{ food }}</div>
  </div>
</template>