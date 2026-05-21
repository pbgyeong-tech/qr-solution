<template>
  <button
    :class="['ui-gnb-action-button', `ui-gnb-action-button--${state}`]"
    v-bind="$attrs"
  >
    <img :src="icon" class="ui-gnb-action-button__icon" alt="" />
  </button>
</template>

<script setup>
defineProps({
  icon:  { type: String, required: true },
  /* 'default' | 'hover' | 'selected' */
  state: { type: String, default: 'default' },
})
</script>

<style scoped>
.ui-gnb-action-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 32px;
  height: 32px;
  padding: var(--size-4);
  border: none;
  border-radius: var(--radius-pill);
  background-color: transparent;
  cursor: pointer;
  transition: background-color 0.15s;
}
.ui-gnb-action-button--hover    { background-color: rgba(55, 72, 108, 0.5); }
.ui-gnb-action-button--selected { background-color: rgba(21, 29, 43, 0.7); }

.ui-gnb-action-button__icon {
  width: var(--sizing-icon-lg);   /* 24px */
  height: var(--sizing-icon-lg);
}
</style>
