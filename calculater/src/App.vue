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
    <button @click="minus"></button>
    <div class="border p-2 m-2">{{ data.number }}</div>
    <button @click="plus"></button>
  </div>
</template>