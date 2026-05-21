<template>
  <label :class="['ui-checkbox', { 'ui-checkbox--disabled': disabled }]">
    <span class="ui-checkbox__control">
      <span class="ui-checkbox__box">
        <img v-if="selection === 'checked'"       :src="iconChecked"       class="ui-checkbox__icon" alt="" />
        <img v-else-if="selection === 'indeterminate'" :src="iconIndeterminate" class="ui-checkbox__icon" alt="" />
      </span>
    </span>
    <span class="ui-checkbox__label"><slot /></span>
  </label>
</template>

<script setup>
import iconChecked       from '../../icons/ui/icon=check-box_check.svg'
import iconIndeterminate from '../../icons/ui/icon=check-box_indeterminate.svg'

defineProps({
  /* 'checked' | 'indeterminate' | 'unchecked' */
  selection: { type: String, default: 'unchecked' },
  disabled:  { type: Boolean, default: false },
})
</script>

<style scoped>
.ui-checkbox {
  display: inline-flex;
  align-items: flex-start;
  gap: var(--size-6);
  cursor: pointer;
}
.ui-checkbox--disabled {
  opacity: var(--opacity-disabled);
  cursor: not-allowed;
  pointer-events: none;
}

.ui-checkbox__control {
  display: flex;
  align-items: center;
  padding: 2px;
  flex-shrink: 0;
}
.ui-checkbox__box {
  position: relative;
  width: 16px;
  height: 16px;
  border-radius: var(--radius-tag);  /* 2px */
  border: 1px solid var(--color-control-border);
  overflow: hidden;
}
/* checked / indeterminate → SVG가 박스 전체를 덮어 border 가림 */
.ui-checkbox__box:has(.ui-checkbox__icon) {
  border-color: transparent;
}
.ui-checkbox__icon {
  display: block;
  width: 100%;
  height: 100%;
}

.ui-checkbox__label {
  font-family: var(--font-family-base);
  font-size: var(--font-size-14);
  font-weight: var(--font-weight-regular);
  line-height: var(--line-height-base);
  color: var(--color-text-primary);
  white-space: nowrap;
}
</style>
