<template>

    <button class="button">
      <slot/>
    </button>

</template>

<script>
export default {
  name: 'Button',
  props: {
    title: {type: String, required: true}
  }
}
</script>

<style lang="scss" scoped>

.button {
  border: none;
  width: max-content;
  text-transform: uppercase;
  color: var(--color-button-text);
  background-color: var(--color-primary);
  border-radius: 24px;
  text-decoration: none;
  padding: 16px 32px;
  font-weight: 700;
  font-size: 15px;
  transition: var(--base-transition-timing) var(--base-transition-motion) background-color;
  will-change: background-color;
  outline: none;

  &:hover {
    cursor: pointer;
    background-color: lighten(#41B883, 5%);
  }
}
</style>