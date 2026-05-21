<template>
  <div
    :class="['asset-qr-code', { 'asset-qr-code--hover': isHover }]"
    @mouseenter="isHover = true"
    @mouseleave="isHover = false"
  >
    <!-- QR 이미지 -->
    <img :src="src" :alt="`QR code for ${code}`" class="asset-qr-code__img" />

    <!-- 제품 코드 라벨 (default: 이미지 하단, hover: 이미지 내 좌하단) -->
    <span :class="['asset-qr-code__code', isHover ? 'asset-qr-code__code--inner' : 'asset-qr-code__code--below']">
      {{ code }}
    </span>

    <!-- hover 오버레이: 검색 아이콘 -->
    <div v-if="isHover" class="asset-qr-code__overlay">
      <img :src="searchIcon" class="asset-qr-code__search-icon" alt="" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import searchIcon from '../../icons/ui/icon=search.svg'

defineProps({
  src:  { type: String, default: '' },   /* QR 코드 이미지 URL */
  code: { type: String, default: '' },   /* 제품 코드 (예: VR9700D) */
})

const isHover = ref(false)
</script>

<style scoped>
.asset-qr-code {
  position: relative;
  width: 40px;
  height: 40px;
  flex-shrink: 0;
  cursor: pointer;
}

/* QR 이미지 */
.asset-qr-code__img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: var(--radius-tag);   /* 2px */
  pointer-events: none;
}

/* 제품 코드 라벨 */
.asset-qr-code__code {
  font-family: var(--font-family-base);
  font-size: var(--font-size-11);
  font-weight: var(--font-weight-regular);
  line-height: var(--line-height-base);
  white-space: nowrap;
  color: var(--color-text-secondary);
}
.asset-qr-code__code--below {
  /* QR 이미지 바로 아래 */
  position: absolute;
  left: var(--size-4);
  top: calc(100% + 2px);
}
.asset-qr-code__code--inner {
  /* hover 시 QR 이미지 좌하단 내부 */
  position: absolute;
  left: 10%;
  bottom: 0;
  font-size: 2.5px;   /* Figma 원본값 유지 — QR 내 라벨 */
  color: #000;
}

/* hover 오버레이: 우하단 검색 아이콘 pill */
.asset-qr-code__overlay {
  position: absolute;
  right: 10%;
  bottom: 10%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2px;
  border-radius: var(--radius-pill);
  background-color: rgba(21, 29, 43, 0.8);
}
.asset-qr-code__search-icon {
  width: 12px;
  height: 12px;
}
</style>
