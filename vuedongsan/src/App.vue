<template>
  <div>
    <Modal/>

    <div class="menu">
      <a v-for="a in menu" :key="a"> {{ a }} </a>
    </div>

    <Discount/>

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
import oneroomsdata from "./assets/oneroom";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";

export default {
  name: "App",

  data() {
    return {
      clicked: 0,
      onerooms: oneroomsdata,
      modal: false,
      menu: ["Home", "Shop", "About"],
    };
  },
  created() {},
  methods: {},
  components: {
    Discount,
    Modal
  },
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 15px;
}
</style>
