<script setup>
defineProps({
  src: {
    type: String,
    required: true,
  },
  color: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <view class="inner-icon-box">
    <image class="inner-icon" :src="src" :style="{ filter: `drop-shadow(750rpx 0 0 ${color})` }" />
  </view>
</template>

<style scoped>
.inner-icon-box {
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.inner-icon {
  box-sizing: content-box;
  display: block;
  width: 100%;
  height: 100%;
  border-right: 100000px solid transparent;
  transform: translateX(-750rpx);
}

/* Safari */
@supports (-webkit-hyphens: none) {
  .inner-icon {
    will-change: transform;
  }
}
</style>
