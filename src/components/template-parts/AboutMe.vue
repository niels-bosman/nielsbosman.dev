<template>
  <section class="content about-me has-text" @mousemove="mouseMovement">
    <div class="container about">
      <h2 class="heading" :style="{'transform': `translate(${right()}px`}">
        Over mij<highlight>.</highlight>
      </h2>
      <article :style="{'transform': `translate(${left()}px`}">
        <p class="text">
          Hoi! Mijn naam is Niels Bosman. Ik ben <highlight>{{getAge()}} jaar oud</highlight> en ik woon in Ede.
          Momenteel zit ik in mijn tweede jaar van mijn studie <highlight>HBO-ICT</highlight> op de Hogeschool van Arnhem en Nijmegen waarbij mijn uitstroomprofiel <highlight>Webdevelopment</highlight> is. Dit betekend dat ik hierdoor mijn kennis voor het onwikkelen van web-oplossingen kan vebreden 👨🏼‍💻.
        </p>
        <p class="text">
          Naast mijn opleiding ben ik in mijn vrije tijd veel bezig met het ontwikkelen van hobby-projecten op het gebied van Webdevelopment en werk ik ook als <highlight>Freelance Webdeveloper</highlight>.
        </p>
      </article>
    </div>
  </section>
</template>

<script>
import Highlight from '../helpers/Highlight'

export default {
  name: 'AboutMe',
  components: { Highlight },
  data() {
    return {
      birthDate: new Date(2000, 2, 1),
      diffX: 0,
      diffXModifier: 100,
    }
  },
  methods: {
    getAge() {
      const diffInMs = Date.now() - this.birthDate.getTime()
      const ageDate = new Date(diffInMs)

      return Math.abs(ageDate.getUTCFullYear() - 1970)
    },
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

<style scoped lang="scss">
@import "src/assets/scss/mixins";

.text {
  @include fluidFontSize(14px, 20px);
  line-height: 2;
  font-weight: 500;
  color: var(--color-light);
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;
  max-width: 900px;
  margin: 0 0 40px 0;

  &:last-child {
    margin: 0;
  }
}

.heading {
  color: var(--color-lightest);
  margin: 0 0 40px;
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;
}

.content {
  position: relative;
  display: grid;
  background: var(--color-dark-lighter);
  transition: var(--base-transition-timing) var(--base-transition-motion) background;
  will-change: background;

  @media (max-width: 1200px) {
    padding: 100px 15px;
  }

  @media (max-width: 700px) {
    padding: 50px 15px;
  }

  &:after {
    content: "ABOUT" !important;
  }
}

.about {
  z-index: 1;
}
</style>