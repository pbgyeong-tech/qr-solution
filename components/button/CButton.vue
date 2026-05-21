<template>
  <button
    :class="classes"
    :disabled="disabled"
    v-bind="$attrs"
  >
    <img v-if="iconLeft" :src="iconLeft" class="c-button__icon" alt="" />
    <span class="c-button__label"><slot /></span>
    <img v-if="iconRight" :src="iconRight" class="c-button__icon" alt="" />
  </button>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  /* 'btn' = filled (button/default), 'text' = text-button */
  type: {
    type: String,
    default: 'btn',
    validator: (v) => ['btn', 'text'].includes(v),
  },
  /* primary / secondary / tertiary(text only) */
  importance: {
    type: String,
    default: 'primary',
    validator: (v) => ['primary', 'secondary', 'tertiary'].includes(v),
  },
  /* large / medium / small  (text type은 size 없음) */
  size: {
    type: String,
    default: 'large',
    validator: (v) => ['large', 'medium', 'small'].includes(v),
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  iconLeft: {
    type: String,
    default: null,
  },
  iconRight: {
    type: String,
    default: null,
  },
})

const classes = computed(() => [
  'c-button',
  `c-button--${props.type}`,
  `c-button--${props.importance}`,
  props.type === 'btn' && `c-button--${props.size}`,
  { 'c-button--disabled': props.disabled },
])
</script>

<style scoped>
/* ── 공통 기반 ── */
.c-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--size-4);
  border: none;
  cursor: pointer;
  white-space: nowrap;
  border-radius: var(--radius-component);
  transition: background-color 0.15s;
}
.c-button--disabled {
  opacity: var(--opacity-disabled);
  cursor: not-allowed;
  pointer-events: none;
}
.c-button__icon {
  flex-shrink: 0;
}

/* ══ type: btn (filled) ══ */

/* size */
.c-button--btn.c-button--large {
  height: var(--sizing-control-lg);       /* 45px */
  padding: 0 var(--size-16);
  font-family: var(--font-family-base);
  font-size: var(--font-size-16);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-snug);
}
.c-button--btn.c-button--large .c-button__icon {
  width: var(--sizing-icon-md);           /* 20px */
  height: var(--sizing-icon-md);
}

.c-button--btn.c-button--medium {
  height: 32px;
  padding: 0 var(--size-12);
  font-family: var(--font-family-base);
  font-size: var(--font-size-12);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-snug);
}
.c-button--btn.c-button--medium .c-button__icon {
  width: var(--sizing-icon-sm);           /* 16px */
  height: var(--sizing-icon-sm);
}

.c-button--btn.c-button--small {
  height: 26px;
  padding: 0 var(--size-10);
  font-family: var(--font-family-base);
  font-size: 10px;
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-snug);
}
.c-button--btn.c-button--small .c-button__icon {
  width: var(--sizing-icon-sm);           /* 16px */
  height: var(--sizing-icon-sm);
}

/* importance — btn */
.c-button--btn.c-button--primary {
  background-color: var(--color-brand-primary);
  color: var(--color-text-on-btn);
}
.c-button--btn.c-button--primary:hover:not(.c-button--disabled) {
  background-color: var(--color-brand-primary-hover);
}

.c-button--btn.c-button--secondary {
  background-color: var(--color-bg-interactive);
  color: var(--color-text-primary);
}
.c-button--btn.c-button--secondary:hover:not(.c-button--disabled) {
  background-color: var(--color-bg-interactive-hover);
}

/* ══ type: text (text-button) ══ */
.c-button--text {
  background-color: transparent;
  padding: var(--size-2) var(--size-4);
  border-radius: var(--radius-hit-area);
  font-family: var(--font-family-base);
  font-size: var(--font-size-14);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-snug);
}
.c-button--text .c-button__icon {
  width: var(--sizing-icon-sm);           /* 16px */
  height: var(--sizing-icon-sm);
}

/* importance — text */
.c-button--text.c-button--primary {
  color: var(--color-text-btn-primary);
}
.c-button--text.c-button--primary:hover:not(.c-button--disabled) {
  background-color: var(--color-bg-btn-text-hover);
}

.c-button--text.c-button--secondary {
  color: var(--color-text-btn-secondary);
}
.c-button--text.c-button--secondary:hover:not(.c-button--disabled) {
  background-color: var(--color-bg-btn-text-hover);
}

.c-button--text.c-button--tertiary {
  color: var(--color-text-muted);
}
</style>
