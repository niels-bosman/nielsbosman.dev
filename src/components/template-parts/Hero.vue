<template>
  <div class="hero" @mousemove="mouseMovement">
    <article class="content">
      <p class="subtitle" :style="{'transform': `translate(${left()}px`}">
        Hoi 👋, ik ben
      </p>
      <h1 class="heading" :style="{'transform': `translate(${right()}px`}">
        Niels Bosman<highlight>.</highlight>
      </h1>
      <p class="subtitle" :style="{'transform': `translate(${left()}px`}">
        Webontwikkelaar
        <highlight>&</highlight>
        student
      </p>
    </article>
    <scroll-button/>
  </div>
</template>

<script>

import Highlight from '../helpers/Highlight'
import ScrollButton from '../buttons/ScrollButton'

export default {
  name: 'Hero',
  components: { Highlight, ScrollButton },
  data() {
    return {
      diffX: 0,
      diffXModifier: 100,
    }
  },
  methods: {
    mouseMovement(event) {
      this.diffX = event.clientX - window.innerWidth / 2;
    },
    left() {
      return this.diffX / this.diffXModifier
    },
    right() {
      return this.left() * -1
    },
  },
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
  will-change: background;

  &:after {
    @include fluidFontSize(10em, 30em);
    content: "HALLO";
    position: absolute;
    font-weight: 900;
    color: var(--color-light);
    transition: var(--base-transition-timing) var(--base-transition-motion) color;
    will-change: color;
    opacity: 4%;
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
  font-family: 'Lato Black', sans-serif;
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;
  line-height: .9;

  @media screen and (max-width: 900px) {
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

  @media screen and (max-width: 900px) {
    text-align: center;
    font-weight: 700;
  }
}

</style>