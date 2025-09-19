<script setup>
import { ref } from 'vue'
import SubOne from './sub-one.vue'
import SubTwo from './sub-two.vue'

const index = ref(0)

const onToggle = () => {
  index.value = index.value === 0 ? 1 : 0
}

const imageList = [
  'https://placehold.co/690x200?text=1',
  'https://placehold.co/690x200?text=2',
  'https://placehold.co/690x200?text=3',
  'https://placehold.co/690x200?text=4',
  'https://placehold.co/690x200?text=5',
]
</script>

<template>
  <swiper
    autoplay
    circular
    class="swiper"
    :duration="500"
    :interval="2000"
    vertical
    @change="onChange"
  >
    <swiper-item v-for="image in imageList" :key="image" class="swiper-item">
      <image class="image" :src="image" />
    </swiper-item>
  </swiper>

  <button class="btn" @click="onToggle">切换组件</button>

  <SubOne v-if="index === 0" />
  <SubTwo v-else />
</template>

<style scoped>
:global(page) {
  min-height: 100vh;
  padding: 30rpx;
  box-sizing: border-box;
}

.btn {
  margin: 30rpx auto;
}

.swiper {
  width: 690rpx;
  height: 200rpx;
}

.swiper-item {
  width: 100%;
  height: 100%;
}

.image {
  width: 100%;
  height: 100%;
}
</style>
