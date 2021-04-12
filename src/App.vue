<template>
  <main :class="[isDark ? 'dark' : 'light']">
    <control-panel :is-dark="isDark" @switch="isDark = !isDark"/>
    <hero/>
    <about-me/>
    <experience/>
    <technologies/>
    <projects/>
  </main>
</template>

<script>
import ControlPanel from './components/atoms/ControlPanel'
import Hero from './components/template-parts/Hero'
import AboutMe from "./components/template-parts/AboutMe";
import Experience from "./components/template-parts/Experience";
import Technologies from "./components/template-parts/Technologies";
import Projects from "./components/template-parts/Projects";

export default {
  name: 'App',
  components: { ControlPanel, Hero, AboutMe, Experience, Technologies, Projects },
  data() {
    return { isDark: true }
  },
  methods: {
    OSIsDark() {
      return window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches
    },
  },
  created() {
    // Base theme on currently set theme. Else base it on the OS theme.
    const storedTheme = window.localStorage.getItem('theme')
    this.isDark = storedTheme !== null ? storedTheme === 'dark' : this.OSIsDark()
    window.localStorage.setItem('isDark', this.isDark ? 'dark' : 'light')
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;600;700;900&display=swap');
@import "assets/scss/mixins";
@import "assets/scss/container";

$color-canvas-dark-1: #31323a;
$color-canvas-dark-2: #4e5065;
$color-canvas-dark-3: #25262f;

$color-canvas-light-1: #FFF;
$color-canvas-light-2: #DBDBDB;
$color-canvas-light-3: #e4e4e4;

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
  --color-lightest: #{$color-canvas-dark-1};

  --color-dark: #{$color-canvas-light-2};
  --color-dark-light: #{$color-canvas-light-1};
  --color-dark-lighter: #{$color-canvas-light-3};

  --color-light-dark: #000000;
}

::selection {
  background: var(--color-dark-light);
  color: var(--color-light);
}

body {
  margin: 0;
  padding: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h1, h2, h3, h4, h5, h6 {
  word-wrap: break-word;
  font-family: 'Lato Black', sans-serif;
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

h1, h2, h3, h4, h5, h6, p, span {
  &:hover {
    cursor: default;
  }
}

.has-text {

  &:after {
    max-width: 100vw;
    overflow-x: hidden;
    @include fluidFontSize(8em, 25em);
    position: absolute;
    font-weight: 900;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    color: transparent;
    transition: var(--base-transition-timing) var(--base-transition-motion) -webkit-text-stroke;
    will-change: color;
    opacity: 1%;
    -webkit-text-stroke: 7px var(--color-light-dark);

    @media (max-width: 900px) {
      -webkit-text-stroke-width: 4px;
    }
  }
}
</style>