<template>
  <div class="technology">
    <div class="technology-icon">
      <slot/>
    </div>
    <h5 class="technology-heading">
      {{ name }}
    </h5>
  </div>
</template>

<script>
export default {
  name: 'TechnologyCard',
  props: {
    name: { type: String, required: true },
    data() {
      return { hoverState: false }
    },
  },
}
</script>

<style lang="scss">
@import "../../assets/scss/mixins";

.technology {
  min-width: 112px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  margin-right: 40px;
  margin-bottom: 40px;
  background: var(--color-lightest);
  border-radius: 10px;
  box-shadow: 0 0 20px -10px rgb(0 0 0 / 40%);
  transition: var(--base-transition-timing) var(--base-transition-motion) background, var(--base-transition-timing) var(--base-transition-motion) transform;
  will-change: transform, background;

  .has-hovered-card & .technology-icon {
    filter: grayscale(100%);
  }

  &:hover {
    cursor: pointer;
    transform: translateY(-10px);

    .technology-icon {
      filter: grayscale(0) !important;
    }
  }

  .technology-heading {
    @include fluidFontSize(1rem, 1.4rem);
    color: var(--color-dark);
    font-weight: 900;
    margin: 20px 0 0 0;
    transition: var(--base-transition-timing) var(--base-transition-motion) color;
    will-change: color;
    text-align: center;
  }

  .technology-icon {
    height: 100px;
    width: 100px;
    transition: var(--base-transition-timing) var(--base-transition-motion) filter;
    will-change: filter;
  }
}
</style>