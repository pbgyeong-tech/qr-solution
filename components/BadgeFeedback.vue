<template>
  <div class="badge-feedback">
    <img :src="checkIcon" class="badge-feedback__icon" alt="" />
  </div>
</template>

<script setup>
import checkIcon from '../icons/ui/icon=check.svg'
</script>

<style scoped>
.badge-feedback {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 60px;
  border-radius: var(--radius-pill);
  background-color: var(--color-status-approve-bg);
}
.badge-feedback__icon {
  width: var(--sizing-icon-xl);   /* 40px */
  height: var(--sizing-icon-xl);
}
</style>
