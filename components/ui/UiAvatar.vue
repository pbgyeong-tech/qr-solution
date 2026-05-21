<template>
  <div :class="['ui-avatar', `ui-avatar--${role}`, `ui-avatar--${size}`]">
    <span class="ui-avatar__inner">
      <span class="ui-avatar__initial">{{ initial }}</span>
    </span>
  </div>
</template>

<script setup>
/*
 * role  : 'local-manager' | 'regional-manager' | 'product-manager' | 'system-manager'
 * size  : 'large'(40px) | 'small'(36px) | 'small-selected'(36px + outline)
 * initial: 표시할 이니셜 (예: 'J')
 */
defineProps({
  role:    { type: String, default: 'local-manager' },
  size:    { type: String, default: 'large' },
  initial: { type: String, default: 'J' },
})
</script>

<style scoped>
/* ── 공통 ── */
.ui-avatar {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--radius-pill);
  overflow: hidden;
  flex-shrink: 0;
}
.ui-avatar__inner {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  border-radius: var(--radius-pill);
}
.ui-avatar__initial {
  font-family: var(--font-family-base);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-snug);
  color: var(--color-text-primary);
  text-align: center;
}

/* ── size ── */
.ui-avatar--large {
  width: 40px;
  height: 40px;
}
.ui-avatar--large .ui-avatar__initial { font-size: var(--font-size-16); }

.ui-avatar--small,
.ui-avatar--small-selected {
  width: 36px;
  height: 36px;
  padding: 2px;
}
.ui-avatar--small .ui-avatar__initial,
.ui-avatar--small-selected .ui-avatar__initial { font-size: var(--font-size-14); }

/* small-selected: 외곽 링 효과 */
.ui-avatar--small-selected {
  background-color: var(--color-text-muted);  /* #91a3c5 outer ring */
}

/* ── role — 배경색 ── */
.ui-avatar--local-manager    .ui-avatar__inner { background-color: var(--color-avatar-purple); }
.ui-avatar--regional-manager .ui-avatar__inner { background-color: var(--color-avatar-blue); }
.ui-avatar--product-manager  .ui-avatar__inner { background-color: var(--color-avatar-blue); }
.ui-avatar--system-manager   .ui-avatar__inner { background-color: var(--color-avatar-green); }
</style>
