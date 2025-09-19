<script setup>
import { ref } from 'vue'
import SubOne from './sub-one.vue'
import SubTwo from './sub-two.vue'

const isOne = ref(true)
</script>

<template>
  <button class="btn" @click="isOne = !isOne">Toggle</button>
  <SubOne v-if="isOne" />
  <SubTwo v-else />
</template>

<style scoped>
:global(page) {
  box-sizing: border-box;
  min-height: 100vh;
  padding: 30rpx;
}

.btn {
  margin: 30rpx auto;
}
</style>
