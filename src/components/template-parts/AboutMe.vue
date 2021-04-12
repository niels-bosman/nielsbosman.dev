<template>
  <section class="content about-me has-text" @mousemove="mouseMovement">
    <div class="container about">
      <h2 class="heading" :style="{'transform': `translate(${right()}px`}">
        Over mij<highlight>.</highlight>
      </h2>
      <div class="under" :style="{'transform': `translate(${left()}px`}">
        <article>
          <p class="text">
            Hoi! Mijn naam is Niels Bosman. Ik ben
            <highlight>{{ getAge() }} jaar oud</highlight>
            en ik woon in Ede.
            Momenteel zit ik in mijn tweede jaar van mijn studie
            <highlight>HBO-ICT</highlight>
            op de Hogeschool van Arnhem en Nijmegen waarbij mijn uitstroomprofiel
            <highlight>Webdevelopment</highlight>
            is. Dit betekend dat ik hierdoor mijn kennis van het onwikkelen van web-oplossingen kan vebreden 👨🏼‍💻.
            Deze opleiding volg ik als uitbreiding op mijn vooroplaiding <highlight>Software Development</highlight> op het Graafschap College in Doetinchem.
          </p>
          <p class="text">
            Naast mijn opleiding ben ik in mijn vrije tijd veel bezig met het ontwikkelen van hobby-projecten op het
            gebied van Webdevelopment en ook werk ik als
            <highlight>Freelance Webontwikkelaar</highlight>.
          </p>
        </article>
        <figure class="image">
          <picture>
            <source srcset="../../../public/me.webp" type="image/webp">
            <source srcset="../../../public/me.jpeg" type="image/jpeg">
            <img src="../../../public/me.jpeg" alt="Niels Bosman">
          </picture>
        </figure>
      </div>
    </div>
  </section>
</template>

<script>
import Highlight from '../atoms/Highlight'
import { isMobile } from 'mobile-device-detect'

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
      if (!isMobile) {
        this.diffX = event.clientX - window.innerWidth / 2
      }
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

.image {
  border-radius: 50%;
  max-width: 300px;
  max-height: 300px;
  overflow: hidden;

  @media (max-width: 1300px) {
    max-width: 250px;
    max-height: 250px;
    margin-top: 60px;
  }

  img {
    object-fit: cover;
    width: 100%;
  }
}
.under {
  display: flex;

  @media (max-width: 1300px) {
    flex-direction: column;
  }

  @media (max-width: 900px) {
    align-items: center;
  }
}

.text {
  font-size: 20px;
  line-height: 2;
  font-weight: 500;
  color: var(--color-light);
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;
  max-width: 900px;
  margin: 0 0 40px 0;

  @media (max-width: 1300px) {
    font-size: 16px;
  }

  &:last-child {
    margin: 0;
  }
}

.heading {
  color: var(--color-lightest);
  margin: 0 0 20px;
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;

  @media (max-width: 700px) {
    margin: 0 0 25px;
  }
}

.content {
  position: relative;
  display: grid;
  background: var(--color-dark-lighter);
  transition: var(--base-transition-timing) var(--base-transition-motion) background;
  will-change: background;
  padding: 150px 0;

  @media (max-width: 1200px) {
    padding: 100px 15px;
  }

  @media (max-width: 700px) {
    padding: 65px 15px;
  }

  &:after {
    content: "ABOUT" !important;
  }
}

.about {
  z-index: 1;
}
</style>