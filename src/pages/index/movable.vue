<script setup>
import { ref } from 'vue'

const movableX = ref(0)

function onMovableChange(e) {
  movableX.value = e.detail.x
}
</script>

<template>
  <movable-area class="movable-area" direction="horizontal">
    <movable-view
      class="movable-view"
      direction="horizontal"
      :x="movableX"
      @change="onMovableChange"
    />
  </movable-area>
</template>

<style scoped>
.movable-area {
  position: relative;
  width: 400rpx;
  height: 96rpx;
  margin: 40rpx auto;
  background: #eee;
}

.movable-view {
  width: 96rpx;
  height: 96rpx;
  background: #121212;
  border-radius: 50%;
}
</style>
