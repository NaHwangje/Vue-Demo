<script setup>
import { reactive, computed } from "vue";

const data = reactive({
  // 값 저장
  number: 0,
  temp: 0,
  operator: null,
  log: "",
});

function inputNumber(number) {
  // 숫자 대입시 적용
  if (data.number == 0) data.number = number;
  else data.number = data.number * 10 + number;
}

function inputOperator(value) {
  data.temp = data.number; //기호 눌릴시 입력 값 임시 값으로 이동
  data.number = 0;
  data.operator = value; //기호를 data,operator에 대입
}

const displayed = computed(() => {
  let text = "";
  if (data.temp) text += data.temp; //temp에 값이 있을 시 text에 문자열로 값 추가
  if (data.operator) text += data.operator; // operator에 있는 기호 추가
  if (data.number) text += data.number; // number에 있는 값 추가
  if (!text) text = 0; //text안에 아무것도 없으면 0 출력
  return text; //컴퓨트 함수로 계산 된 값 출력
});

function calculate() {
  let result = eval(displayed.value);
  data.log = data.log + eval(displayed.value) + "\n"; // 계산 완료된 값을 기록에 남김
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
  //키보드 입력 받는 함수
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
  //로그 남기는 함수
  if (temp) {
    if (data.log === null) {
      data.log = temp;
    } else {
      data.log += eval(displayed.value) + "\n" + data.operator + " " + temp;
    }
  } else {
    data.log = null;
  }
}

document.addEventListener("keyup", getKey); //함수 실행기
</script>

<template>
  <div>
    <div class="grid grid-cols-6 gap-4">
      <div class="col-span-6 texxt-center text-2xl font-bold">계산기</div>
      <div
        class="col-span-4 border p-4 text-right rounded-lg bg-white text-black"
      >
        {{ displayed }}
        <!-- 디스플레이  -->
      </div>
      <!-- 로그 메뉴 -->
      <span class="grid grid-span-2 text-3xl text-right">Logs</span>
      <!-- 숫자패드 -->
      <div class="col-span-3 grid grid-cols-3 gap-4">
        <button v-for="n of 9" v-bind:key="n" @click="inputNumber(n)">
          {{ n }}
        </button>
        <button @click="inputNumber(0)">0</button>
        <button @click="reset">C</button>
        <button @click="calculate">=</button>
      </div>
      <!-- 기호패드 -->
      <div class="col-span-1 grid gap-4">
        <button
          v-for="o of ['+', '-', '*', '/']"
          v-bind:key="o"
          @click="inputOperator(o)"
        >
          {{ o }}
        </button>
      </div>
      <!-- 로그박스 -->
      <div
        class="col-span-2 grid border p-4 text-right rounded-lg bg-white text-black"
        style="white-space: pre-line"
      >
        {{ data.log }}
      </div>
    </div>
  </div>
</template>