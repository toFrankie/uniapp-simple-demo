<script setup>
import { ref } from 'vue'
import SubOne from './sub-one.vue'
import SubTwo from './sub-two.vue'

const mode = ref(0)

const onModeChange = nextMode => {
  mode.value = nextMode
}
</script>

<template>
  <button class="btn" @click="onModeChange(Number(!mode))">切换模式</button>
  <SubOne v-if="mode === 0" />
  <SubTwo v-else />
</template>

<style scoped>
:global(page) {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  width: 100vw;
}

.btn {
  margin: 30rpx;
}
</style>
