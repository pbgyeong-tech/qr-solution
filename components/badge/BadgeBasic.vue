<template>
  <!-- type: status -->
  <div v-if="type === 'status'" :class="statusClasses">
    <span :class="statusTextClasses">{{ statusLabel }}</span>
  </div>

  <!-- type: visibility -->
  <div v-else-if="type === 'visibility'" class="badge-visibility">
    <img :src="visibilityIcon" class="badge-visibility__icon" alt="" />
    <span :class="visibilityTextClass">{{ status === 'public' ? 'Public' : 'Private' }}</span>
  </div>

  <!-- type: account-status -->
  <div v-else-if="type === 'account-status'" class="badge-account">
    <span :class="['badge-account__dot', `badge-account__dot--${status}`]" />
    <span class="badge-account__label">{{ accountLabel }}</span>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import publicIcon  from '../icons/ui/icon=public.svg'
import privateIcon from '../icons/ui/icon=private.svg'

const props = defineProps({
  type: {
    type: String,
    default: 'status',
    validator: (v) => ['status', 'visibility', 'account-status'].includes(v),
  },
  /*
   * status     : 'published' | 'draft' | 'pending' | 'rejected'
   * visibility : 'public' | 'private'
   * account    : 'active' | 'inactive' | 'deleted'
   */
  status: {
    type: String,
    required: true,
  },
  /* status type 전용: 'large'(default) | 'small' */
  size: {
    type: String,
    default: 'large',
    validator: (v) => ['large', 'small'].includes(v),
  },
})

/* ── status ── */
const statusClasses = computed(() => [
  'badge-status',
  `badge-status--${props.status}`,
  `badge-status--${props.size}`,
])

const statusTextClasses = computed(() => [
  'badge-status__label',
  `badge-status__label--${props.status}`,
  `badge-status__label--${props.size}`,
])

const statusLabel = computed(() => ({
  published: 'Published',
  draft:     'Draft',
  pending:   'Pending Review',
  rejected:  'Rejected',
}[props.status] ?? props.status))

/* ── visibility ── */
const visibilityIcon = computed(() =>
  props.status === 'public' ? publicIcon : privateIcon
)
const visibilityTextClass = computed(() => [
  'badge-visibility__label',
  `badge-visibility__label--${props.status}`,
])

/* ── account-status ── */
const accountLabel = computed(() => ({
  active:   'Active',
  inactive: 'Inactive',
  deleted:  'Deleted',
}[props.status] ?? props.status))
</script>

<style scoped>
/* ══ type: status ══ */
.badge-status {
  display: inline-flex;
  align-items: center;
  border-radius: 16px;
}

/* size */
.badge-status--large {
  height: 23px;
  padding: 3px 6px 2px;
}
.badge-status--small {
  height: 17px;
  padding: 1px 4px;
}

/* state — background */
.badge-status--published { background-color: var(--color-status-approve-bg); }
.badge-status--pending   { background-color: var(--color-status-pending-bg); }
.badge-status--rejected  { background-color: var(--color-status-reject-bg); }
.badge-status--draft     { background-color: var(--color-bg-tertiary); }

/* label */
.badge-status__label {
  font-family: var(--font-family-base);
  font-weight: var(--font-weight-regular);
  line-height: var(--line-height-snug);
  white-space: nowrap;
}
.badge-status__label--large { font-size: var(--font-size-13); }
.badge-status__label--small { font-size: var(--font-size-11); }

.badge-status__label--published { color: var(--color-status-approve-text); }
.badge-status__label--pending   { color: var(--color-status-pending-text); }
.badge-status__label--rejected  { color: var(--color-status-reject-text); }
.badge-status__label--draft     { color: var(--color-text-secondary); }

/* ══ type: visibility ══ */
.badge-visibility {
  display: inline-flex;
  align-items: center;
  gap: var(--size-2);
  height: 18px;
}
.badge-visibility__icon {
  width: var(--sizing-icon-sm);   /* 16px */
  height: var(--sizing-icon-sm);
  flex-shrink: 0;
}
.badge-visibility__label {
  font-family: var(--font-family-base);
  font-size: var(--font-size-13);
  font-weight: var(--font-weight-regular);
  line-height: var(--line-height-snug);
}
.badge-visibility__label--public  { color: var(--color-text-btn-primary); }
.badge-visibility__label--private { color: var(--color-text-muted); }

/* ══ type: account-status ══ */
.badge-account {
  display: inline-flex;
  align-items: center;
  gap: var(--size-8);
  height: 18px;
}
.badge-account__dot {
  display: inline-block;
  width: 10px;
  height: 10px;
  border-radius: var(--radius-pill);
  flex-shrink: 0;
}
.badge-account__dot--active   { background-color: var(--color-status-dot-active); }
.badge-account__dot--inactive { background-color: var(--color-status-dot-inactive); }
.badge-account__dot--deleted  { background-color: var(--color-status-dot-deleted); }

.badge-account__label {
  font-family: var(--font-family-base);
  font-size: var(--font-size-13);
  font-weight: var(--font-weight-regular);
  line-height: var(--line-height-snug);
  color: var(--color-text-secondary);
}
</style>
