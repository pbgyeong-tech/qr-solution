<template>
  <div class="form-label">
    <span class="form-label__text"><slot /></span>
    <span v-if="necessary" class="form-label__required" aria-hidden="true">*</span>
    <img v-if="tooltip" :src="infoIcon" class="form-label__tooltip-icon" alt="도움말" />
  </div>
</template>

<script setup>
import infoIcon from '../../icons/ui/icon=info.svg'

/*
 * necessary : 필수 항목 여부 → 빨간 * 표시
 * tooltip   : 툴팁 아이콘 표시 여부
 * 라벨 텍스트는 slot으로 전달
 */
defineProps({
  necessary: { type: Boolean, default: false },
  tooltip:   { type: Boolean, default: false },
})
</script>

<style scoped>
.form-label {
  display: inline-flex;
  align-items: center;
  gap: var(--size-2);
  height: 18px;
}

.form-label__text {
  font-family: var(--font-family-base);
  font-size: var(--font-size-14);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-snug);
  color: var(--color-text-secondary);
  white-space: nowrap;
}

.form-label__required {
  font-family: var(--font-family-base);
  font-size: var(--font-size-14);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-snug);
  color: var(--color-status-reject-text);  /* #ef3434 */
}

.form-label__tooltip-icon {
  width: var(--sizing-icon-sm);   /* 16px */
  height: var(--sizing-icon-sm);
  flex-shrink: 0;
}
</style>
