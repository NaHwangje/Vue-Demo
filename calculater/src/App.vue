<script setup>
import { reactive, computed } from "vue";

const data = reactive({
  number: 0,
  temp: 0,
  operator: null,
  log: "",
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
  let text = "";
  if (data.temp) text += data.temp;
  if (data.operator) text += data.operator;
  if (data.number) text += data.number;
  if (!text) text = 0;
  return text ;
});

function calculate() {
  let result = eval(displayed.value);
  data.temp = 0;
  data.operator = null;
  data.number = result;
}

function reset() {
  data.temp = 0;
  data.operator = null;
  data.number = 0;
}

function getKey(event) {
  if (event.key.match(/[0-9]/)) {
    inputNumber(event.key * 1);
  } else if (["+", "-", "*", "/"].includes(event.key)) {
    inputOperator(event.key);
  } else if (event.key == "=" || event.key == "Enter") {
    calculate();
  } else if (event.key == "C" || event.key == "Esc") {
    reset();
  }
}
function log(temp) {
  if (temp) {
    if (data.log === null) {
      data.log = temp;
    } else {
      data.log += " " + data.operator + " " + temp;
    } 
  } else{
    data.log = null
  }
}

document.addEventListener("keyup", getKey);
</script>

<template>
  <div>
    <div class="grid grid-cols-6 gap-4">
      <div class="col-span-5 texxt-center text-2xl font-bold">계산기</div>
      <div
        class="col-span-6 border p-4 text-right rounded-lg bg-white text-black"
      >
        {{ displayed }}
      </div>

      <div class="col-span-3 grid grid-cols-3 gap-4">
        <button v-for="n of 9" v-bind:key="n" @click="inputNumber(n)">
          {{ n }}
        </button>
        <button @click="inputNumber(0)">0</button>
        <button @click="reset">C</button>
        <button @click="calculate">=</button>
      </div>

      <div class="col-span-1 grid gap-4">
        <button
          v-for="o of ['+', '-', '*', '/']"
          v-bind:key="o"
          @click="inputOperator(o)"
        >
          {{ o }}
        </button>
      </div>

      <div
        class="col-span-2 grid border p-4 text-right rounded-lg bg-white text-black "
      >
        {{ data.log }}
      </div>
    </div>
  </div>
</template>