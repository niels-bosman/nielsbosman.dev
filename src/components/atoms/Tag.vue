<template>
  <aside>
    <slot/>
  </aside>
</template>

<script>
export default {
  name: 'Tag'
}
</script>

<style scoped lang="scss">
aside {
  display: inline;
  padding: 8px 20px;
  background: var(--color-primary);
  border-radius: 17px;
  font-size: 18px;
  font-weight: 900;
  color: #FFF;

  @media (max-width: 950px) {
    padding: 6px 16px;
    display: block;
    width: fit-content;
    margin: 0;
  }
}
</style>