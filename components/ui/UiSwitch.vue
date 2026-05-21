<template>
  <button
    role="switch"
    :aria-checked="modelValue"
    :class="['ui-switch', modelValue ? 'ui-switch--on' : 'ui-switch--off', { 'ui-switch--disabled': disabled }]"
    :disabled="disabled"
    @click="$emit('update:modelValue', !modelValue)"
  >
    <span class="ui-switch__thumb" />
  </button>
</template>

<script setup>
defineProps({
  modelValue: { type: Boolean, default: false },
  disabled:   { type: Boolean, default: false },
})
defineEmits(['update:modelValue'])
</script>

<style scoped>
.ui-switch {
  display: inline-flex;
  align-items: center;
  width: 36px;
  height: 20px;
  padding: 2px;
  border: none;
  border-radius: var(--radius-pill);
  cursor: pointer;
  transition: background-color 0.2s;
}
.ui-switch--on  { background-color: var(--color-control-selected); justify-content: flex-end; }
.ui-switch--off { background-color: var(--color-control-track);    justify-content: flex-start; }
.ui-switch--disabled {
  opacity: var(--opacity-disabled);
  cursor: not-allowed;
  pointer-events: none;
}

.ui-switch__thumb {
  display: block;
  width: 16px;
  height: 16px;
  border-radius: var(--radius-pill);
  background-color: var(--color-text-on-btn);  /* white */
  flex-shrink: 0;
}
</style>
