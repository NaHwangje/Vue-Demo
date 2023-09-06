<template>
  <div>
    <div class="menu">
      <a v-for="a in menu" :key="a"> {{ a }} </a>
    </div>

    <div v-for="(b, i) in 3" :key="b">
      <img
        src="https://i.namu.wiki/i/MdIcQe5C3YFThD4FzDu9zoYYdRE4SpcGfb9cagDWVzn-a3cPR9TdMf1rF9Rk9zLDCZRZWD8ZIRKLi8c74CeLRPvaQNChqnrFtJ3uejTG5CvdHWX45xlEbgjQfGcC4VRgonFgHbRISx2bKOQiDjwang.webp"
        class="room-img"
      />
      <h4>{{ products[i] }}</h4>
      <p>{{ price[i] }} 만원</p>
      <button @click="신고수++">허위매물 신고</button> <span>신고 수 : {{ 신고수 }} </span>
      <!-- @ == v-on -->
    </div>
  </div>
</template>
 
<script>
export default {
  name: "App",
  data() {
    return {
      신고수 : 0,
      price: [60, 80, 90],
      products: ["상대동원룸", "하대동원룸", "상평동원룸"],
      menu: ["Home", "Shop", "About"],
    };
  },
  components: {},
};
</script>

<style>
.room-img {
  width: 70%;
  margin-top: 15px;
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
