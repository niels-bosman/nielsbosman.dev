<template>
  <section class="experience has-text">
    <div class="container" id="experience-scene">
      <h2 class="heading" data-depth="0.8">
        Ervaring<highlight>.</highlight>
      </h2>
      <div class="items" id="experience-section">
        <div v-for="experience in experiences"
             :key="experience.title"
             class="item"
             :data-depth="experience.depth"
        >
          <h3 class="item-title">
            {{ experience.title }}
            <highlight>&vert;</highlight>
            {{ experience.jobTitle }}
            <tag class="tag">{{ experience.start }} &dash; {{ experience.end }}</tag>
          </h3>
          <article>
            <p>{{ experience.description }}</p>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Highlight from '../atoms/Highlight'
import Tag from '../atoms/Tag'

export default {
  name: 'Experience',
  components: { Highlight, Tag },
  data() {
    return {
      experiences: {
        dtcMedia: {
          title: 'DTC Media Online',
          depth: '0.3',
          jobTitle: 'Front-end developer',
          start: 'okt. 2019',
          end: 'heden',
          description: 'Het ontwikkelen, aanpassen en onderhouden van websites en webapplicaties voor de automotive branche. Hierbij heb ik gewerkt met Wordpress, Vue.js en Laravel.'
        },
        riff: {
          title: 'RIFF Digital Engagement',
          depth: '0.5',
          jobTitle: 'Front-end developer',
          start: 'jan. 2019',
          end: 'okt. 2019',
          description: 'Het maken van maatwerk Wordpress websites en webshops voor een grote hoeveelheid klanten. Hierbij gebruik gemaakt van PHP, JavaScript en SCSS.'

        },
        brandpepper: {
          title: 'Brandpepper',
          depth: '0.2',
          jobTitle: 'Stagiair Wordpress Development',
          start: 'aug. 2018',
          end: 'jan. 2019',
          description: 'Tijdens deze stage kennisgemaakt met het werken in Scrum en het leren van de Atlassian Toolstack voor het ontwikkelen van software. Hiernaast ook kennis gemaakt met thema-ontwikkeling in Wordpress.'
        },
      }
    }
  },
}
</script>

<style scoped lang="scss">
@import "../../assets/scss/mixins";

.experience {
  position: relative;
  display: flex;
  flex-direction: column;
  background: var(--color-dark);
  transition: var(--base-transition-timing) var(--base-transition-motion) background;
  will-change: background;
  padding: 120px 0;

  &:after {
    content: "WORK";
  }

  @media (max-width: 1200px) {
    padding: 100px 0;
  }

  @media (max-width: 700px) {
    padding: 50px 0;
  }
}

.container {
  z-index: 1;
}

.heading {
  text-align: center;
  font-weight: 900;
  margin: 0;
  color: var(--color-lightest);
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;
  line-height: .9;
  position: relative !important;
}

.items {
  margin-top: 90px;
  position: relative !important;

  @media (max-width: 600px) {
    margin-top: 50px;
  }
}

.item {
  margin-bottom: 70px;
  position: relative !important;

  &:last-child {
    margin-bottom: 0;
  }
}

.item-title {
  @include fluidFontSize(1.3em, 1.5em);
  color: var(--color-lightest);
  font-weight: 900;
  font-family: 'Lato', sans-serif;
  margin: 0 0 30px 0;
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;

  @media (max-width: 900px) {
    margin: 0 0 15px 0;
  }
}

article {
  line-height: 2;
  font-size: 20px;
  font-weight: 500;
  color: var(--color-light);
  max-width: 900px;
  z-index: 1;
  transition: var(--base-transition-timing) var(--base-transition-motion) color;
  will-change: color;

  @media (max-width: 1300px) {
    font-size: 16px;
  }

  p {
    margin: 0;
  }
}

.tag {
  margin-left: 10px;

  @media (max-width: 950px) {
    margin: 20px 0;
  }
}
</style>