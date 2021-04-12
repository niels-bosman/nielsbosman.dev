<template>
  <span>
    <slot/>
  </span>
</template>

<script>
export default { name: 'Highlight' }
</script>

<style scoped lang="scss">
span {
  color: var(--color-primary);
  font-weight: 900;
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;

  &:hover {
    color: var(--color-secondary);
  }
}
</style>