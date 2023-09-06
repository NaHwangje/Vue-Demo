<template>
  <div>
    <div class="menu">
      <a v-for="a in menu" :key="a"> {{ a }} </a>
    </div>

    <div v-for="(b, i) in products" :key="b">
      <img :src="imageUrls[i]" class="room-img" />
      <h4>{{ products[i] }}</h4>
      <p>{{ price[i] }} 만원</p>
      <button @click="신고수++">허위매물 신고</button>
      <span>신고 수 : {{ 신고수 }} </span>
      <!-- @ == v-on -->
    </div>
  </div>
</template>
 
<script>
export default {
  name: "App",
  data() {
    return {
      신고수: 0,
      price: [60, 80, 90],
      products: ["상대동원룸", "하대동원룸", "상평동원룸"],
      menu: ["Home", "Shop", "About"],
      imageUrls: [],
    };
  },
  created() {
    // 이미지 폴더 내 모든 이미지 가져오기
    const imageContext = require.context(
      "./assets",
      false,
      /\.(png|jpe?g|gif|svg)$/
    );

    // 이미지 경로 배열 생성
    this.imageUrls = imageContext.keys().map(imageContext);
  },
  methods: {
    async loadImagesFromFolder(folderPath) {
      // 폴더 내의 이미지 파일을 가져오기 위해 HTTP 요청을 보낼 수 있습니다.
      // 예를 들어, 서버에서 해당 폴더 내의 이미지 목록을 제공하는 API를 호출할 수 있습니다.
      try {
        const response = await fetch(
          `/api/get-images?folderPath=${folderPath}`
        );
        if (response.ok) {
          const data = await response.json();
          this.imageUrls = data.imageUrls;
        } else {
          console.error("이미지 가져오기 실패");
        }
      } catch (error) {
        console.error("이미지 가져오기 오류:", error);
      }
    },
  },
  components: {},
};
</script>

<style>
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
