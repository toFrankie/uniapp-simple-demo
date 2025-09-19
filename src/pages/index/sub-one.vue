<script setup>
/**
 * 问题描述：编译到 iOS App 端，各 swiper-item 重叠在一起。
 */

import { onMounted, ref } from 'vue'
import { FAKE_LIST } from '../../constants'

const list = ref([])

onMounted(async () => {
  list.value = await fetchList()
})

function fetchList() {
  return new Promise(resolve => setTimeout(() => resolve(FAKE_LIST), 1000))
}

function onChange(e) {
  console.log('🚀 ~ onChange ~ e:', e.detail.source, e.detail.current)
}
</script>

<template>
  <view class="subtitle">组件一</view>

  <swiper
    autoplay
    circular
    class="swiper"
    :duration="200"
    :interval="2000"
    vertical
    @change="onChange"
  >
    <swiper-item v-for="text in list" :key="text" class="swiper-item">
      {{ text }}
    </swiper-item>
  </swiper>
</template>

<style scoped>
.subtitle {
  font-size: 24px;
  font-weight: bold;
}

.swiper {
  margin-bottom: 30rpx;
  background: #eee;
  border-radius: 10rpx;
  width: 100%;
  height: 72rpx;
}

.swiper-item {
  width: 100%;
  height: 100%;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  display: flex;
  align-items: center;
}
</style>
