<template>
  <label :class="['ui-radio', { 'ui-radio--disabled': disabled }]">
    <span class="ui-radio__control">
      <span class="ui-radio__outer" :class="{ 'ui-radio__outer--selected': modelValue }">
        <span v-if="modelValue" class="ui-radio__dot" />
      </span>
    </span>
    <span class="ui-radio__label"><slot /></span>
  </label>
</template>

<script setup>
defineProps({
  modelValue: { type: Boolean, default: false },
  disabled:   { type: Boolean, default: false },
})
defineEmits(['update:modelValue'])
</script>

<style scoped>
.ui-radio {
  display: inline-flex;
  align-items: center;
  gap: var(--size-6);
  cursor: pointer;
}
.ui-radio--disabled {
  opacity: var(--opacity-disabled);
  cursor: not-allowed;
  pointer-events: none;
}

.ui-radio__control {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2px;
  flex-shrink: 0;
}
.ui-radio__outer {
  width: 16px;
  height: 16px;
  border-radius: var(--radius-pill);
  border: 1px solid var(--color-control-border);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}
.ui-radio__outer--selected {
  border-color: var(--color-control-selected);
}
.ui-radio__dot {
  width: 8px;
  height: 8px;
  border-radius: var(--radius-pill);
  background-color: var(--color-control-selected);
}

.ui-radio__label {
  font-family: var(--font-family-base);
  font-size: var(--font-size-14);
  font-weight: var(--font-weight-regular);
  line-height: var(--line-height-base);
  color: var(--color-text-primary);
  white-space: nowrap;
}
</style>
