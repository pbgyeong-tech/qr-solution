<template>
  <div :class="['asset-thumbnail', `asset-thumbnail--${size}`]">
    <img
      :src="src"
      :alt="alt"
      class="asset-thumbnail__img"
    />
  </div>
</template>

<script setup>
/*
 * size : 'medium'(48px) | 'large'(90px)
 * src  : 썸네일 이미지 URL
 */
defineProps({
  size: { type: String, default: 'medium', validator: (v) => ['medium', 'large'].includes(v) },
  src:  { type: String, default: '' },
  alt:  { type: String, default: '' },
})
</script>

<style scoped>
.asset-thumbnail {
  position: relative;
  border-radius: var(--radius-component);   /* 4px */
  overflow: hidden;
  flex-shrink: 0;
  background-color: var(--color-bg-tertiary);
}

.asset-thumbnail--medium {
  width: 48px;
  height: 48px;
}
.asset-thumbnail--large {
  width: 90px;
  height: 90px;
  padding: var(--size-8);
}

.asset-thumbnail__img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: contain;
  pointer-events: none;
}
</style>
