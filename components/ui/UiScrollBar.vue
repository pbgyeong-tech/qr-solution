<template>
  <div class="ui-scroll-bar">
    <div
      class="ui-scroll-bar__thumb"
      :style="{ height: thumbHeight + '%', top: thumbTop + '%' }"
    />
  </div>
</template>

<script setup>
defineProps({
  /* 전체 콘텐츠 대비 뷰포트 비율 0~1 */
  ratio:    { type: Number, default: 0.3 },
  /* 스크롤 위치 0~1 */
  position: { type: Number, default: 0 },
})

import { computed } from 'vue'

const props = defineProps({
  ratio:    { type: Number, default: 0.3 },
  position: { type: Number, default: 0 },
})

const thumbHeight = computed(() => Math.max(props.ratio * 100, 10))
const thumbTop    = computed(() => props.position * (100 - thumbHeight.value))
</script>

<style scoped>
.ui-scroll-bar {
  position: relative;
  width: 4px;
  border-radius: 2px;
  background-color: transparent;
}
.ui-scroll-bar__thumb {
  position: absolute;
  left: 0;
  width: 4px;
  border-radius: 2px;
  background-color: var(--color-border-default);
}
</style>
