<template>
  <div class="badge-number">
    <span class="badge-number__label">{{ count > 99 ? '99+' : count }}</span>
  </div>
</template>

<script setup>
defineProps({
  count: {
    type: Number,
    default: 1,
  },
})
</script>

<style scoped>
.badge-number {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-width: 20px;
  height: 20px;
  padding: 4px 6px;
  border-radius: 28px;
  background-color: var(--color-blue-900);
}
.badge-number__label {
  font-family: var(--font-family-base);
  font-size: var(--font-size-12);
  font-weight: var(--font-weight-bold);
  line-height: 1;
  color: var(--color-text-on-btn);
}
</style>
