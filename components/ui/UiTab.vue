<template>
  <div class="ui-tab">
    <slot />
  </div>
</template>

<style scoped>
.ui-tab {
  display: flex;
  align-items: flex-end;
  border-bottom: 1px solid var(--color-border-subtle);
}
</style>
