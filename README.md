### 跑马灯抽奖

```vue
<script>
import { ref } from 'vue';
import LuckyGrid from './components/packages/LuckyGrid.vue';
const prizes = [{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
},
{
  img: 'https://img.yzcdn.cn/vant/apple-1.jpg',
  name: '苹果'
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
```