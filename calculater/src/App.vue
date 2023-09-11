<script setup>
import { reactive } from 'vue';

const data = reactive({
 number: 0
})

function increment(){
  data.number++
}
</script>

<template>
  <div>
<div>{{ data.number }}</div>
<div>{{ b }}</div>
<button @click="increment">증가</button>
  </div>
</template> 