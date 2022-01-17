<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import { ref } from 'vue';
import LuckyGrid from './components/packages/LuckyGrid.vue';
const prizes = [{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
}]

const luckyGrid = ref(null)
const start = () => {
  console.log('start')
  luckyGrid.value.start()
  setTimeout(() => {
    luckyGrid.value.stop()
  }, 3000);
}
const luckyStop = (reward) => {
  console.log('stop', reward)
}
</script>

<template>
<LuckyGrid ref="luckyGrid" :prizes="prizes" @stop="luckyStop" />
<button @click="start">开始</button>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
