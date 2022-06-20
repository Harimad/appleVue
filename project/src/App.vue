<template>
  <p>{{ msg }}</p>
  <!-- <p v-for="n in 10">{{ n }}</p> -->
  <p v-for="상품 in products" :key="상품">{{ 상품 }}</p>
  <div class="menu">
    <a v-for="(메뉴, i) in menus" :key="i">{{ i }}: {{ 메뉴 }}</a>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      msg: 'hello word',
      products: ['군자동원룸', ' 송정동원룸', '능동원룸'],
      menus: ['Home', 'About', 'Shop'],
    }
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
  margin-top: 60px;
}

.menu {
  background-color: aqua;
  padding: 20px;
}
.menu a {
  padding-right: 10px;
}
</style>
