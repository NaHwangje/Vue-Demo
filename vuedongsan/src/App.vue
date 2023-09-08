<template>
  <div>
    <!-- <div class="black-bg" v-if="모달창열렸니 == true">
      <div class="white-bg">
        <h4>상세 페이지</h4>
        <p>상세 페이지 내용임</p>
        <button @click="모달창열렸니 = false">x</button>
      </div>
    </div> -->
    <div class="menu">
      <a v-for="a in menu" :key="a"> {{ a }} </a>
    </div>

    <div v-for="(n,i) in onerooms " :key="n">
      <img :src="onerooms[i].image" class="room-img" />

      <h4 @click="모달창열렸니 = true">{{ onerooms[i].title }}</h4>

      <p>{{ onerooms[i].price }} 만원</p>
      
    </div>
  </div>
</template>


<script>
import oneroomsdata from './assets/oneroom'

export default {
  name: "App",
  data() {
    return {
     onerooms: oneroomsdata,
      모달창열렸니: false,
      menu: ["Home", "Shop", "About"],
    };
  },
  created() {},
  methods: {},
  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
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
