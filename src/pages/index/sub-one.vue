<script setup>
// https://github.com/dcloudio/uni-app/issues/5354

import Swiper from './swiper.vue'
import Movable from './movable.vue'
</script>

<template>
  <view class="subtitle">子组件一</view>
  <Swiper />
  <Movable />
</template>

<style scoped>
.subtitle {
  font-size: 24px;
  font-weight: bold;
}
</style>
