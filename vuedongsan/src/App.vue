<template>
  <div class="menu"> 
    <a v-for="a in menu" :key="a"> {{a}} </a>
  </div>

  <div v-for="b in products" :key="b">
    <h4 >{{ b }}</h4>
    <p > 100 만원</p>
  </div>



</template>
 
<script>
export default {
  name: "App",
  data() {
    return {
      price : [60, 80, 90],
      products : ['상대동원룸', '하대동원룸', '상평동원룸'],
      menu : ['Home', 'Shop', 'About']
    };
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background: darkslateblue;
  padding: auto;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: auto;
}
</style>
