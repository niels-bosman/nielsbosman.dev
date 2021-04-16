<template>
  <main :class="[isDark ? 'dark' : 'light']">
    <control-panel :is-dark="isDark" @switch="isDark = !isDark"/>
    <hero/>
    <about-me/>
    <experience/>
    <technologies/>
  </main>
</template>

<script>
import ControlPanel from './components/atoms/ControlPanel'
import Hero from './components/template-parts/Hero'
import AboutMe from './components/template-parts/AboutMe'
import Experience from './components/template-parts/Experience'
import Technologies from './components/template-parts/Technologies'
import {isMobile} from 'mobile-device-detect'
import Parallax from 'parallax-js'

export default {
  name: 'App',
  components: { ControlPanel, Hero, AboutMe, Experience, Technologies },
  data() {
    return { isDark: true }
  },
  methods: {
    OSIsDark() {
      return window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches
    },
    setTheme(isDark) {
      this.isDark = isDark
      window.localStorage.setItem('isDark', isDark ? 'dark' : 'light')
    }
  },
  created() {
    // Set the change of color scheme change event so it changes when user changes it.
    window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', e => {
      this.setTheme(e.matches === 'dark')
    })

    // Set vh variable for mobile 100% height on hero.
    const vh = window.innerHeight * 0.01
    document.documentElement.style.setProperty('--vh', `${vh}px`)

    // Base theme on currently set theme. Else base it on the OS theme.
    const storedTheme = window.localStorage.getItem('theme')
    const wantsToBeDark = storedTheme !== null ? storedTheme === 'dark' : this.OSIsDark()
    this.setTheme(wantsToBeDark)
  },
  mounted() {
    if (isMobile) return

    // Define base settings for parallax.
    const settings = { frictionY: 0, frictionX: 0.05, scalarX: 1.5, pointerEvents: true, invertX: false }

    // Define all scenes.
    const elements = [
      'hero-scene',
      'about-me-heading-scene',
      'about-me-text-scene',
      'experience-scene',
      'experience-section',
      'technology-scene'
    ]

    // Instantiate parallax scenes.
    elements.forEach(id => new Parallax(document.getElementById(id), settings))
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;600;700;900&display=swap');
@import "assets/scss/mixins";
@import "assets/scss/container";
@import "assets/scss/font-awesome";

$color-canvas-dark-1: #2A2B33;
$color-canvas-dark-2: #4E5065;
$color-canvas-dark-3: #25262F;

$color-canvas-light-1: #FFF;
$color-canvas-light-2: #EFEFEF;
$color-canvas-light-3: #E4E4E4;

:root {
  --color-dark: #{$color-canvas-dark-1};
  --color-dark-light: #{$color-canvas-dark-2};
  --color-dark-lighter: #{$color-canvas-dark-3};

  --color-light: #{$color-canvas-light-2};
  --color-lightest: #{$color-canvas-light-1};

  --color-light-dark: #FFF;

  --color-button-text: #{$color-canvas-light-1};
  --color-primary: #41B883;
  --color-secondary: #B84176;

  --base-transition-timing: .4s;
  --base-transition-motion: ease;
}

.light {
  --color-light: #{$color-canvas-dark-2};
  --color-lightest: #{$color-canvas-dark-2};

  --color-dark: #{$color-canvas-light-2};
  --color-dark-light: #{$color-canvas-light-1};
  --color-dark-lighter: #{$color-canvas-light-3};

  --color-light-dark: #{$color-canvas-dark-1};
}

::selection {
  background: var(--color-dark-light);
}

body {
  margin: 0;
  padding: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h1, h2, h3, h4, h5, h6 {
  word-wrap: break-word;
  color: var(--color-dark);
  font-weight: 900;
}

h2 {
  @include fluidFontSize(4rem, 6rem);
  margin: 20px 0;
}

* {
  font-family: 'Lato', sans-serif;
}

.has-text {
  max-width: 100vw;
  overflow-x: hidden;
  &:hover:after {
    color: transparent;
  }

  &:after {
    @include fluidFontSize(8em, 25em);
    max-width: 100vw;
    overflow-x: hidden;
    position: absolute;
    font-weight: 900;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    color: var(--color-light-dark);
    transition: .8s var(--base-transition-motion) color, -webkit-text-stroke;
    will-change: color;
    -webkit-text-stroke: var(--color-light-dark) 7px;
    opacity: 0.04;

    @media (max-width: 900px) {
      -webkit-text-stroke-width: 4px;
    }

    @media (max-width: 500px) {
      display: none;
    }
  }
}
</style>