<template>
  <div class="menu">
    <a v-for="(메뉴, i) in menus" :key="i">{{ 메뉴 }}</a>
  </div>
  <div v-for="(상품, i) in products" :key="상품">
    <p>{{ products[i] }}</p>
    <button @click="increase(i)">허위매물신고</button>
    <span> {{ 신고수[i] }}</span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      신고수: [0, 1, 2],
      products: ['군자동원룸', ' 송정동원룸', '능동원룸'],
      menus: ['Home', 'About', 'Shop'],
    }
  },
  methods: {
    increase(i) {
      this.신고수[i]++
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background-color: aqua;
  padding: 20px;
  border-radius: 20px;
}
.menu a {
  padding-right: 10px;
}
</style>
