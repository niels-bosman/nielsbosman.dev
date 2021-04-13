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
@import "../../assets/scss/mixins";

aside {
  @include fluidFontSize(16px, 18px);
  display: inline;
  padding: 6px 16px;
  background: var(--color-dark-light);
  border-radius: 17px;
  font-weight: 900;
  color: var(--color-light);
  transition: var(--base-transition-timing) var(--base-transition-motion) background, color;
  will-change: background, color;

  @media (max-width: 950px) {
    padding: 6px 16px;
    display: block;
    width: fit-content;
    margin: 0;
  }
}
</style>