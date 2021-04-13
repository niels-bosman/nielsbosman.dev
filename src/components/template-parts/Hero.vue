<template>
  <section class="hero has-text">
    <socials/>
    <section class="content" id="hero-scene" data-relative-input="true">
      <p class="subtitle" data-depth="0.2">
        Hoi 👋🏻, ik ben
      </p>
      <h1 class="heading" data-depth="0.8">
        Niels Bosman<highlight>.</highlight>
      </h1>
      <h2 class="subtitle" data-depth="0.2">
        Webontwikkelaar
        <highlight>&</highlight>
        student
      </h2>
    </section>
    <scroll-button/>
  </section>
</template>

<script>
import Highlight from '../atoms/Highlight'
import ScrollButton from '../buttons/ScrollButton'
import Socials from '../atoms/Socials'

export default {
  name: 'Hero',
  components: { Highlight, ScrollButton, Socials },
}
</script>

<style lang="scss" scoped>
@import "../../assets/scss/mixins";

.hero {
  display: grid;
  place-items: center;
  position: relative;
  height: calc(var(--vh, 1vh) * 100);
  background: var(--color-dark);
  transition: var(--base-transition-timing) var(--base-transition-motion) background;
  will-change: background;

  &:after {
    content: "HELLO";
  }
}

.content {
  padding: 20px;
  display: flex;
  flex-direction: column;
  z-index: 1;
}

.heading {
  @include fluidFontSize(4em, 8em);
  font-weight: 900;
  margin: 20px 0;
  color: var(--color-lightest);
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;
  line-height: .9;
  display: inline !important;
  position: relative !important;

  @media (max-width: 900px) {
    text-align: center;
  }
}

.subtitle {
  @include fluidFontSize(1.4em, 2em);
  font-weight: 900;
  margin: 0;
  color: var(--color-light);
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;
  display: inline !important;
  position: relative !important;

  &:last-child {
    text-align: right;
  }

  @media (max-width: 900px) {
    text-align: center !important;
    font-weight: 700;
  }
}
</style>