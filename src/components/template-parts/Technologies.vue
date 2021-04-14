<template>
  <section class="content has-text">
    <div class="container" id="technology-scene">
      <h2 class="heading" data-depth="0.8">
        Technologieën<highlight>.</highlight>
      </h2>
      <article class="text" data-depth="0.2">
        <p>Hier een opsomming van <highlight>technologieën</highlight> en <highlight>tools</highlight> waar ik ervaring mee heb. Dit zijn programmeertalen, libraries en frameworks.</p>
      </article>
      <section class="technologies" :class="{'has-hovered-card': hoverActive}" data-depth="0.4">
        <technology-card name="Vue"
                         @mouseenter="hoverActive = true"
                         @mouseleave="hoverActive = false"
        >
          <img src="../../../public/vue.svg" alt="Laravel" loading="lazy">
        </technology-card>
        <technology-card name="Laravel"
                         @mouseenter="hoverActive = true"
                         @mouseleave="hoverActive = false"
        >
          <img src="../../../public/laravel.svg" alt="Laravel" loading="lazy">
        </technology-card>
        <technology-card name="Java"
                         @mouseenter="hoverActive = true"
                         @mouseleave="hoverActive = false"
        >
          <img src="../../../public/java.svg" alt="Java" loading="lazy">
        </technology-card>
        <technology-card name="PHP"
                         @mouseenter="hoverActive = true"
                         @mouseleave="hoverActive = false"
        >
          <img src="../../../public/php.svg" alt="Java" loading="lazy">
        </technology-card>
        <technology-card name="JavaScript"
                         @mouseenter="hoverActive = true"
                         @mouseleave="hoverActive = false"
        >
          <img src="../../../public/javascript.svg" alt="Java" loading="lazy">
        </technology-card>
        <technology-card name="SASS"
                         @mouseenter="hoverActive = true"
                         @mouseleave="hoverActive = false"
        >
          <img src="../../../public/scss.svg" alt="SASS" loading="lazy">
        </technology-card>
        <technology-card name="Wordpress"
                         @mouseenter="hoverActive = true"
                         @mouseleave="hoverActive = false"
        >
          <img src="../../../public/wordpress.svg" alt="Java" loading="lazy">
        </technology-card>
        <technology-card name="Git"
                         @mouseenter="hoverActive = true"
                         @mouseleave="hoverActive = false"
        >
          <img src="../../../public/git.svg" alt="Git" loading="lazy">
        </technology-card>
      </section>
    </div>
  </section>
</template>

<script>
import Highlight from '../atoms/Highlight'
import TechnologyCard from '../atoms/TechnologyCard'

export default {
  name: 'Technologies',
  components: { Highlight, TechnologyCard },
  data() {
    return {
      hoverActive: false
    }
  },
}
</script>

<style scoped lang="scss">
@import "../../assets/scss/mixins";

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
    padding: 50px 15px;
  }

  &:after {
    content: "TECH" !important;
  }
}

.text {
  position: relative !important;
  color: var(--color-light);
  font-weight: 500;
  font-size: 20px;
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;

  @media (max-width: 1300px) {
    font-size: 16px;
  }
}

.heading {
  color: var(--color-lightest);
  margin: 0 0 20px;
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;
  position: relative !important;

  @media (max-width: 700px) {
    margin: 0 0 25px;
    text-align: center;
  }
}

.has-text:after {
  content: "TECH";
}

.technologies {
  position: relative !important;
  display: flex !important;
  margin-top: 50px;
  flex-wrap: wrap;
}

.container {
  z-index: 1;
}

img {
  width: 100%;
  height: 100%;
}
</style>