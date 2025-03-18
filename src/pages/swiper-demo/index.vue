<script setup>
import { ref } from 'vue'
import SubOne from './sub-one.vue'
import SubTwo from './sub-two.vue'

const index = ref(0)

const onToggle = () => {
  index.value = index.value === 0 ? 1 : 0
}
</script>

<template>
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
  margin-bottom: 30rpx;
}
</style>
