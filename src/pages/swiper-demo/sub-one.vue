<script setup>
/**
 * 问题描述：
 * 验证 iOS App 下在切换页面的时候，会重叠在一起。
 * 观察现象：切换后动画没生效，一直停滞，导致 transform 没有应用上。
 */
const list = [
  // 诗经 蒹葭
  '蒹葭苍苍，白露为霜。所谓伊人，在水一方。溯洄从之，道阻且长。溯游从之，宛在水中央。',
  // 诗经 关雎
  '关关雎鸠，在河之洲。窈窕淑女，君子好逑。',
  // 诗经 桃夭
  '桃之夭夭，灼灼其华。之子于归，宜其室家。',
  // 诗经 汉广
]

function onChange(e) {
  console.log('🚀 ~ onChange ~ e:', e.detail.source, e.detail.current)
}
</script>

<template>
  <view class="box">
    <swiper
      autoplay
      circular
      class="swiper-box"
      :duration="200"
      :interval="3000"
      vertical
      @change="onChange"
    >
      <swiper-item v-for="text in list" :key="text" class="swiper-item" @click="navToCustomService">
        {{ text }}
      </swiper-item>
    </swiper>
  </view>
</template>

<style scoped>
.box {
  height: 36rpx;
  font-size: 22rpx;
  font-weight: 400;
  line-height: 36rpx;
}

.swiper-box {
  width: 100%;
  height: 100%;
}

.swiper-item {
  width: 100%;
  height: 100%;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>
