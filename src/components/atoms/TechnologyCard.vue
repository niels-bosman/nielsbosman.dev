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
  min-width: 90px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  margin-right: 20px;
  margin-bottom: 20px;
  background: #FFF;
  border-radius: 10px;
  transition: var(--base-transition-timing) var(--base-transition-motion) background, var(--base-transition-timing) var(--base-transition-motion) transform, var(--base-transition-timing) var(--base-transition-motion) box-shadow;
  will-change: transform, background;

  .has-hovered-card & {
    .technology-icon {
      filter: grayscale(100%);
      opacity: 0.6;
    }
  }

  &:hover {
    cursor: pointer;
    transform: translateY(-10px);
    box-shadow: 0 0 20px -10px rgb(0 0 0 / 40%);

    .technology-icon {
      filter: grayscale(0) !important;
      opacity: 1 !important;
    }
  }

  .technology-heading {
    @include fluidFontSize(1rem, 1rem);
    color: #2a2b33;
    font-weight: 900;
    margin: 15px 0 0 0;
    transition: var(--base-transition-timing) var(--base-transition-motion) color;
    will-change: color, opacity;
    text-align: center;
  }

  .technology-icon {
    height: 70px;
    width: 70px;
    transition: var(--base-transition-timing) var(--base-transition-motion) filter, var(--base-transition-timing) var(--base-transition-motion) opacity;
    will-change: filter;
  }
}
</style>