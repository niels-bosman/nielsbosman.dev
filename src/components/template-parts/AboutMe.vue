<template>
  <section class="content about-me has-text">
    <div class="container about">
      <div id="about-me-heading-scene">
        <h2 class="heading" data-depth="0.6">
          Over mij
          <highlight>.</highlight>
        </h2>
      </div>
      <div class="under" id="about-me-text-scene">
        <article data-depth="-0.2">
          <p class="text">
            Hoi! Mijn naam is Niels Bosman. Ik ben
            <highlight>{{ getAge }} jaar oud</highlight>
            en ik woon in Ede.
            Momenteel zit ik in mijn {{ getYear }} jaar van mijn studie
            <highlight>HBO-ICT</highlight>
            op de Hogeschool van Arnhem en Nijmegen waarbij mijn uitstroomprofiel
            <highlight>Webdevelopment</highlight>
            is. Dit betekend dat ik hierdoor mijn kennis van het onwikkelen van web-oplossingen kan vebreden 👨🏼‍💻.
            Deze opleiding volg ik als uitbreiding op mijn vooropleiding
            <highlight>Software Development</highlight>
            op het Graafschap College in Doetinchem.
          </p>
          <p class="text">
            Naast mijn opleiding ben ik in mijn vrije tijd veel bezig met het ontwikkelen van hobby-projecten op het
            gebied van Webdevelopment en ook werk ik als
            <highlight>Freelance Webontwikkelaar</highlight>.
          </p>
        </article>
        <figure class="image" data-depth="-0.2">
          <picture>
            <source srcset="../../../public/me.webp" type="image/webp">
            <source srcset="../../../public/me.jpeg" type="image/jpeg">
            <img src="../../../public/me.jpeg" alt="Niels Bosman" loading="lazy" width="300" height="300">
          </picture>
        </figure>
      </div>
    </div>
  </section>
</template>

<script>
import Highlight from '../atoms/Highlight'

export default {
  name: 'AboutMe',
  components: { Highlight },
  computed: {
    getAge: () => {
      const diffInMs = Date.now() - new Date(2000, 2, 1).getTime()
      const ageDate = new Date(diffInMs)

      return Math.abs(ageDate.getUTCFullYear() - 1970)
    },
    getYear: () => {
      const currentDate = Date.now()

      if (currentDate > new Date(2021, 2, 1)) {
        return 'tweede'
      } else if (currentDate > new Date(2022, 2, 1)) {
        return 'derde'
      } else {
        return 'vierde'
      }
    }
  }
}
</script>

<style scoped lang="scss">
@import "src/assets/scss/mixins";

.image {
  border-radius: 50%;
  max-width: 300px;
  max-height: 300px;
  overflow: hidden;
  position: relative !important;

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
    text-align: center;
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
    padding: 100px 0;
  }

  @media (max-width: 700px) {
    padding: 50px 0;
  }

  &:after {
    content: "ABOUT" !important;
  }
}

.about {
  z-index: 1;
}
</style>