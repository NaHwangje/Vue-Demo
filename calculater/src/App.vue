<script setup>
import { reactive, computed } from "vue";

const data = reactive({
  number: 0,
  temp: 0,
  operator: null,
});

function inputNumber(number) {
  if (data.number == 0) data.number = number;
  else data.number = data.number * 10 + number;
}
function inputOperator(value) {
  data.temp = data.number;
  data.number = 0;
  data.operator = value;
}
const displayed = computed(() => {
  let text = ''
  if (data.temp) text += data.temp;
  if (data.operator) text += data.operator;
  if (data.number) text += data.number;
  return text;
});

function claculate() {
  let result = eval(displayed.value);
  data.temp = 0
  data.operator = null
  data.number = result
}
</script>

<template>
  <div class="grid grid-cols-4 gap-4">
    <div
      class="col-span-4 border p-4 text-right rounded-lg bg-white text-black"
    >
      {{ displayed }}
    </div>
    <div class="grid grid-cols-3 gap-4 col-span-3">
      <button v-for="n of 9" @click="inputNumber(n)">{{ n }}</button>
      <button @click="inputNumber(0)">0</button>
      <button class="col-span-2" @click="claculate">=</button>
    </div>
    <div class="grid col-span-1 gap-4">
      <button v-for="o of ['+', '-', '*', '/']" @click="inputOperator(o)">
        {{ o }}
      </button>
    </div>
  </div>
</template>