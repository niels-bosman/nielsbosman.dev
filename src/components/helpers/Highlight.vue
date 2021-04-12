<template>
  <span>
    <slot/>
  </span>
</template>

<script>
export default { name: 'Highlight' }
</script>

<style scoped>
span {
  color: var(--color-primary);
  font-weight: 900;
}
</style>