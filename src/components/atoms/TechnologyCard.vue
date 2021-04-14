<template>
  <div class="technology">
    <div class="technology-inner">
      <div class="technology-icon">
        <slot/>
      </div>
      <h5 class="technology-heading">
        {{ name }}
      </h5>
    </div>
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
  padding: 10px;
  width: calc(10% - 20px);

  @media (max-width: 1000px) {
    width: calc(20% - 20px);
  }

  @media (max-width: 700px) {
    width: calc(25% - 20px);
  }

  @media (max-width: 550px) {
    width: calc(33% - 20px);
  }

  @media (max-width: 500px) {
    width: calc(50% - 20px);
  }
}

.technology-inner {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background: #F6F6F6;
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
    transform: translateY(-7px);
    box-shadow: 0 0 20px -10px rgba(0 0 0 / 40%);

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