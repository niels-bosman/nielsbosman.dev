<template>
  <div class="hero">
    <article class="content">
      <p class="subtitle">Hoi 👋, ik ben</p>
      <h1 class="heading">Niels Bosman</h1>
      <p class="subtitle">
        Webontwikkelaar
        <highlight>&</highlight>
        student</p>
    </article>
    <scroll-button/>
  </div>
</template>

<script>

import Highlight from '../helpers/Highlight'
import ScrollButton from '../buttons/ScrollButton'

export default {
  name: 'Hero',

  components: {Highlight, ScrollButton}
}

</script>

<style lang="scss" scoped>

@import "../../assets/scss/mixins";

.hero {
  display: grid;
  place-items: center;
  position: relative;
  height: 100vh;
  background: var(--color-dark);
  transition: var(--base-transition-timing) var(--base-transition-motion) background;

  &:after {
    @include fluidFontSize(10em, 30em);
    content: "HALLO";
    position: absolute;
    font-weight: 900;
    color: var(--color-light);
    transition: var(--base-transition-timing) var(--base-transition-motion) color;
    opacity: 5%;
  }
}

.content {
  padding: 20px;
  display: flex;
  flex-direction: column;
  z-index: 1;
}

.heading {
  @include fluidFontSize(6em, 8em);
  font-weight: 900;
  margin: 20px 0;
  color: var(--color-lightest);
  font-family: 'Lato Black', sans-serif;
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
}

.subtitle {
  @include fluidFontSize(2em, 2em);
  font-weight: 700;
  margin: 0;
  color: var(--color-light);
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
}

</style>