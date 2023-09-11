<script setup>
function action(){
  let a = document.querySelector('#i1').value
  alert(a)
}
</script>

<template>
  <div>
    <input id="i1" class="m-2" type="text">
    <input type="text">
    <button @click="action">버튼</button>
  </div>
</template> 