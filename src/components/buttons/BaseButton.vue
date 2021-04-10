<template>
  <div class="button-wrapper">
    <button class="button">
      <slot/>
    </button>
  </div>
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

.button-wrapper {
  position: absolute;
  right: 50%;
  bottom: 80px;
  transition: .3s ease all;
  will-change: transform;
  z-index: 1;
  transform: translate(50%, 0);

  &:hover {
    transform: translate(50%, -5px);

    .button {
      background-color: lighten(#41B883, 5%);
    }
  }
}

.button {
  border: none;
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
  }
}
</style>