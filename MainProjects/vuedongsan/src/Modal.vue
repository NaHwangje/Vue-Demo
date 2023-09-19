<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <img :src="onerooms[clicked].image" style="width: 100%" />
      <h4>{{ onerooms[clicked].title }}</h4>
      <p>{{ onerooms[clicked].content }}</p>
      <p>{{ onerooms[clicked].price }} 원</p>
      <Discount />
      <!-- <button @click="modal = false">x</button> -->
    </div>
  </div>
</template>

<script>
export default {
    name: 'ModalCard',
    props:{
        clicked : Object,
        onerooms: Array,
        modal: Boolean,
        
    }

}
</script>

<style>
</style>