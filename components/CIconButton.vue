<template>
  <button
    :class="classes"
    :disabled="disabled"
    v-bind="$attrs"
  >
    <img :src="icon" class="c-icon-button__icon" alt="" />
  </button>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  icon: {
    type: String,
    required: true,
  },
  /* large(48px) / small(26px) */
  size: {
    type: String,
    default: 'large',
    validator: (v) => ['large', 'small'].includes(v),
  },
  /* solid / ghost */
  style: {
    type: String,
    default: 'solid',
    validator: (v) => ['solid', 'ghost'].includes(v),
  },
  disabled: {
    type: Boolean,
    default: false,
  },
})

const classes = computed(() => [
  'c-icon-button',
  `c-icon-button--${props.size}`,
  `c-icon-button--${props.style}`,
  { 'c-icon-button--disabled': props.disabled },
])
</script>

<style scoped>
.c-icon-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border: none;
  cursor: pointer;
  border-radius: var(--radius-component);
  transition: background-color 0.15s;
  overflow: hidden;
}
.c-icon-button--disabled {
  opacity: var(--opacity-disabled);
  cursor: not-allowed;
  pointer-events: none;
}
.c-icon-button__icon {
  width: var(--sizing-icon-lg);   /* 24px */
  height: var(--sizing-icon-lg);
  flex-shrink: 0;
}

/* ── size ── */
.c-icon-button--large {
  width: var(--sizing-control-xl);   /* 54px */
  height: var(--sizing-control-xl);
  padding: var(--size-12);
}
.c-icon-button--small {
  width: 26px;
  height: 26px;
}

/* ── style: solid ── */
.c-icon-button--solid {
  background-color: var(--color-bg-interactive);
}
.c-icon-button--solid.c-icon-button--small {
  padding: var(--size-2);
}
.c-icon-button--solid:hover:not(.c-icon-button--disabled) {
  background-color: var(--color-bg-interactive-hover);
}

/* ── style: ghost ── */
.c-icon-button--ghost {
  background-color: transparent;
}
.c-icon-button--ghost.c-icon-button--small {
  padding: var(--size-4);
}
.c-icon-button--ghost:hover:not(.c-icon-button--disabled) {
  background-color: var(--color-bg-interactive);
}
</style>
