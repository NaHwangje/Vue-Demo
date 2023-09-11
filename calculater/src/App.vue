<script setup>
import { reactive } from 'vue';

const data = reactive({
  number: 0
})

function minus(){
  data.number--
}
function plus(){
  data.number++
}
</script>

<template>
  <div class="flex">
    <button @click="minus" class="bg-red-800 text-3xl" >-</button>
    <div class="border p-2 m-2 text-4xl w-32">{{ data.number }}</div>
    <button @click="plus" class="bg-blue-800 text-3xl">+</button>
  </div>
</template>