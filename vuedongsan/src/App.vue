<template>
  <div class="menu">
    <a v-for="a in menu" :key="a"> {{ a }} </a>
  </div>

  <div v-for="b in products" :key="b">
    <img src="https://i.namu.wiki/i/MdIcQe5C3YFThD4FzDu9zoYYdRE4SpcGfb9cagDWVzn-a3cPR9TdMf1rF9Rk9zLDCZRZWD8ZIRKLi8c74CeLRPvaQNChqnrFtJ3uejTG5CvdHWX45xlEbgjQfGcC4VRgonFgHbRISx2bKOQiDjwang.webp" class="room-img">
    <h4>{{ b }}</h4>
    <p>100 만원</p>
  </div>
</template>
 
<script>
export default {
  name: "App",
  data() {
    return {
      price: [60, 80, 90],
      products: ["상대동원룸", "하대동원룸", "상평동원룸"],
      menu: ["Home", "Shop", "About"],
    };
  },
  components: {},
};
</script>

<style>
.room-img{
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
