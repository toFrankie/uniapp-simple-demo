<script setup>
import Sub from './sub.vue'
</script>

<template>
  <view class="box">
    父组件 600 x 600px，红色
    <Sub />
  </view>
</template>

<style scoped>
:global(page) {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.box {
  width: 600rpx;
  height: 600rpx;
  background-color: red;
  margin: 100rpx auto 0;
  color: #fff;
}
</style>
