<template>
  <div :class="['ui-tab-item', { 'ui-tab-item--selected': selected }]">
    <div class="ui-tab-item__content">
      <span class="ui-tab-item__label"><slot /></span>
    </div>
    <div v-if="selected" class="ui-tab-item__line" />
  </div>
</template>

<script setup>
defineProps({
  selected: { type: Boolean, default: false },
})
</script>

<style scoped>
.ui-tab-item {
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  cursor: pointer;
}

.ui-tab-item__content {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: var(--size-4) var(--size-12) var(--size-8);
}

.ui-tab-item__label {
  font-family: var(--font-family-base);
  font-size: var(--font-size-16);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-snug);
  white-space: nowrap;
  color: var(--color-text-muted);
  transition: color 0.15s;
}
.ui-tab-item--selected .ui-tab-item__label {
  color: var(--color-text-btn-primary);
}

/* 선택 indicator — 2px 하단 라인 */
.ui-tab-item__line {
  width: 100%;
  height: 2px;
  background-color: var(--color-text-btn-primary);
  border-radius: 2px 2px 0 0;
}
</style>
