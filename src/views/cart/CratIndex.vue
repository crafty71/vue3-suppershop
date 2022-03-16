<template>
  <Navbar class="cart-nav" />
  <cart-goods-list></cart-goods-list>
  <cart-bottom-bar></cart-bottom-bar>
</template>

<script setup>
import Navbar from './children/CartNavBar.vue'
import CartGoodsList from './children/CartGoodsList.vue'
import CartBottomBar from './children/CartBottomBar'
import { useStore } from 'vuex'

const store = useStore()

const len = localStorage.length // 获取长度
console.log(len) // 输出5
// eslint-disable-next-line no-array-constructor
for (let i = 0; i < len; i++) {
  // 获取key 索引从0开始
  const getKey = localStorage.key(i)
  // 获取key对应的值
  const getVal = localStorage.getItem(getKey)
  // 放进数组
  // eslint-disable-next-line no-const-assign
  store.commit('cartGoodsList', JSON.parse(getVal))
}
</script>

<style lang="less" scoped>
.cart-nav {
  font-weight: 700;
  font-size: 72px;
  color: white;
  background-color: #ff8198;
}
</style>
