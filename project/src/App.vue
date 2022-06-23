<template>
  <!-- 모달창 -->
  <div class="black-bg" v-if="모달창상태">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="modalToggle">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(메뉴, i) in menus" :key="i">{{ 메뉴 }}</a>
  </div>
  <div v-for="(상품, i) in products" :key="상품">
    <img :src="방이미지[i]" class="roomImg" />
    <p @click="modalToggle">{{ products[i] }}</p>
    <button @click="increase(i)">허위매물신고</button>
    <span> {{ 신고수[i] }}</span>
  </div>
</template>
<script>
export default {
  name: 'App',
  data() {
    return {
      모달창상태: false,
      방이미지: [
        require('./assets/images/room0.jpg'),
        require('./assets/images/room1.jpg'),
        require('./assets/images/room2.jpg'),
      ],
      신고수: [0, 1, 2],
      products: ['군자동원룸', ' 송정동원룸', '능동원룸'],
      menus: ['Home', 'About', 'Shop'],
    }
  },
  methods: {
    increase(i) {
      this.신고수[i]++
    },
    modalToggle() {
      if (this.모달창상태) this.모달창상태 = !this.모달창상태
      else this.모달창상태 = !this.모달창상태
    },
  },
}
</script>

<style>
body {
  margin: 0;
  text-align: center;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.menu {
  background-color: aqua;
  padding: 20px;
  border-radius: 20px;
}
.menu a {
  padding-right: 10px;
}

.roomImg {
  width: 80%;
  padding: 20px;
}
</style>
