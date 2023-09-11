<script setup>
import { reactive } from "vue";

const data = reactive({
  number: 0,
});

function inputNumber(number) {
  data.number = number;
}
</script>

<template>
  <div class="grid grid-cols-4 gap-4">
    <div
      class="col-span-4 border p-4 text-right rounded-lg bg-white text-black"
    >
      display
    </div>
    <div class="grid grid-cols-3 gap-4 col-span-3">
      <button v-for="n of 9">{{ n }}</button>
      <button>0</button>
      <button class="col-span-2">=</button>
    </div>
    <div class="grid col-span-1 gap-4">
      <button>+</button>
      <button>-</button>
      <button>*</button>
      <button>/</button>
    </div>
  </div>
</template>