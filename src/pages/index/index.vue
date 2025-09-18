<script>
export default {
  data() {
    return {
      fillColor: '#f00',
      canvasInitialized: false,
    }
  },

  methods: {
    onCanvasInitialized(initialized) {
      this.canvasInitialized = initialized
    },

    updateFillColor() {
      const randomColor = Math.random().toString(16).slice(2, 8)
      this.fillColor = `#${randomColor}`
    },
  },
}
</script>

<script lang="renderjs" module="renderjs">
import { formatAppLog } from '@dcloudio/uni-app'

/**
 * 复现步骤：
 * 看起来只要在 renderjs 中导入了 @dcloudio/uni-app 就会报错（更详细的报错信息，请执行 pnpm run dev:app-plus 在控制台查看）
 * ERROR: No matching export in "node_modules/xxx/vue/dist/vue.runtime.esm-bundler.js" for import "isInSSRComponentSetup"
 * ERROR: No matching export in "node_modules/xxx/vue.runtime.esm-bundler.js" for import "injectHook"
 *
 * 初步原因：
 * uni-app.es.js 中 import 了 vue 的 isInSSRComponentSetup 和 injectHook，但是 vue 指向了 vue.runtime.esm-bundler.js，它并没有导出这两个方法，所以报错了~
 *
 * 说明：
 * 上述 renderjs script 块中 import @dcloudio/uni-app 是为了提供最小复现步骤。
 * 实际应用中，希望在 renderjs script 块中 import 一些 utils 模块方法以尽可能复用逻辑。
 * 但如果 utils 模块导入了 @dcloudio/uni-app 或导入了其他依赖了 @dcloudio/uni-app 的模块，就会报错。
 */

export default {
  data() {
    return {}
  },

  mounted() {
    formatAppLog('warn', 'index.vue', '测试测试')
    this.initAppCanvas()
  },

  methods: {
    initAppCanvas() {
      this.canvasElement = document.querySelector('#canvas .uni-canvas-canvas')
      console.log('🚀 ~ initAppCanvas ~ this.canvasElement:', this.canvasElement)

      if (!this.canvasElement) return

      this.canvasContext = this.canvasElement.getContext('2d')
      this.$ownerInstance.callMethod('onCanvasInitialized', !!this.canvasContext)
      this.drawCanvas()
    },

    drawCanvas(fillColor = '#f00') {
      this.canvasContext.clearRect(0, 0, this.canvasElement.width, this.canvasElement.height)
      this.canvasContext.fillStyle = fillColor
      this.canvasContext.fillRect(0, 0, this.canvasElement.width, this.canvasElement.height)
    },

    onFillColorChange(fillColor) {
      if (!this.canvasContext) return
      this.drawCanvas(fillColor)
    },
  },
}
</script>

<template>
  <canvas id="canvas" canvas-id="canvas" class="canvas" type="2d"></canvas>
  <view :change:prop="renderjs.onFillColorChange" :prop="fillColor" style="display: none"></view>
  <button @click="updateFillColor">更换颜色</button>
</template>

<style scoped>
.canvas {
  width: 100%;
  height: 400rpx;
}

button {
  margin: 30rpx;
}
</style>
