<template>
  <!-- 모달창 -->
  <div class="black-bg" v-if="모달창상태">
    <div class="white-bg">
      <h4>제품명: {{ 원룸들[지금누른번호].title }}</h4>
      <img :src="원룸들[지금누른번호].image" class="roomImg" />
      <p>제품 설명: {{ 원룸들[지금누른번호].content }}</p>
      <p>가격: {{ 원룸들[지금누른번호].price }} 원</p>
      <button @click="modalToggle">닫기</button>
    </div>
  </div>

  <!-- 메뉴창 -->
  <div class="menu">
    <a v-for="메뉴 in menus" :key="메뉴">{{ 메뉴 }}</a>
  </div>

  <!-- 본문 -->
  <div v-for="(원룸, i) in 원룸들" :key="i">
    <p>No. {{ 원룸.id }}</p>
    <p>{{ 원룸.title }}</p>
    <img
      @click="
        modalToggle();
        changeNum(i);
      "
      :src="원룸.image"
      class="roomImg"
    />
    <button @click="increase(i)">허위매물신고</button>
    <span>{{ 신고수[i] }}</span>
    <hr />
  </div>
</template>

<script>
import 데이터 from './assets/data.js';

export default {
  name: 'App',
  data() {
    return {
      지금누른번호: 0,
      모달창상태: false,
      방이미지: [
        require('./assets/images/room0.jpg'),
        require('./assets/images/room1.jpg'),
        require('./assets/images/room2.jpg'),
      ],
      신고수: new Array(데이터.length).fill(0),
      products: ['군자동원룸', ' 송정동원룸', '능동원룸'],
      menus: ['Home', 'About', 'Shop'],
      원룸들: 데이터,
    };
  },
  methods: {
    increase(i) {
      this.신고수[i]++;
    },
    modalToggle(i) {
      if (this.모달창상태) this.모달창상태 = !this.모달창상태;
      else this.모달창상태 = !this.모달창상태;

      this.지금누른번호 = i;
    },
    changeNum(i) {
      this.지금누른번호 = i;
    },
  },
};
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
