<template>
  <div>
    <div v-for="(n, i) in onerooms" :key="i">
      <img :src="n.image" class="room-img" />

      <h4
        @click="
          modal = true;
          clicked = i;
        "
      >
        {{ n.title }}
      </h4>

      <p>{{ n.price }} 만원</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "OneRoomList",
  props: onerooms,
};
</script>

<style>
</style>