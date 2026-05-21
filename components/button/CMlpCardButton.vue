<template>
  <button :class="['c-mlp-card-button', { 'c-mlp-card-button--hover': hover }]" v-bind="$attrs">
    <img :src="chevronIcon" class="c-mlp-card-button__icon" alt="" />
  </button>
</template>

<script setup>
import chevronIcon from '../icons/ui/icon=chevron_right.svg'

defineProps({
  hover: {
    type: Boolean,
    default: false,
  },
})
</script>

<style scoped>
.c-mlp-card-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 24px;
  height: 24px;
  border: none;
  border-radius: var(--radius-pill);
  background-color: transparent;
  cursor: pointer;
  transition: background-color 0.15s;
}
.c-mlp-card-button:hover,
.c-mlp-card-button--hover {
  background-color: var(--color-bg-interactive-hover);
}
.c-mlp-card-button__icon {
  width: var(--sizing-icon-md);   /* 20px */
  height: var(--sizing-icon-md);
}
</style>
