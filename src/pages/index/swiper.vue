<script setup>
const LIST = [
  '蒹葭苍苍，白露为霜。所谓伊人，在水一方。',
  '关关雎鸠，在河之洲。窈窕淑女，君子好逑。',
  '桃之夭夭，灼灼其华。之子于归，宜其室家。',
]
</script>

<template>
  <swiper autoplay circular class="swiper" :duration="200" :interval="2000" vertical>
    <swiper-item v-for="item in LIST" :key="item" class="swiper-item">
      {{ item }}
    </swiper-item>
  </swiper>
</template>

<style scoped>
.swiper {
  width: 100%;
  height: 72rpx;
  margin-bottom: 30rpx;
  background: #eee;
  border-radius: 10rpx;
}

.swiper-item {
  display: flex;
  align-items: center;
  width: 100%;
  height: 100%;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

</style>
