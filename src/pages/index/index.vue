<script setup>
import { ROUTE } from '@/constants'

import ColorfulIcon from './colorful-icon.vue'

function navToSwiperDemo() {
  uni.navigateTo({ url: ROUTE.SWIPER_DEMO })
}
</script>

<template>
  <button class="btn" @click="navToSwiperDemo">前往 Swiper Demo</button>

  <view class="parent-box">
    <ColorfulIcon
      v-bind="$attrs"
      class="icon"
      color="#f00"
      src="https://cloud-minapp-44328.cloud.ifanrusercontent.com/icon-pro-mode-super.svg"
    />
  </view>
</template>

<style scoped>
:global(page) {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.btn {
  margin: 30rpx auto;
}

.box {
  width: 600rpx;
  height: 600rpx;
  background-color: red;
  margin: 100rpx auto 0;
  color: #fff;
}

.parent-box {
  background-color: #eee;
}

.icon {
  width: 56rpx;
  height: 56rpx;
  margin-right: 4rpx;
  display: block;
}
</style>
