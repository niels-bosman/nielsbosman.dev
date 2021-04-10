<template>
  <main :class="isDark ? 'dark' : 'light'">
    <control-panel @switch="setTheme"/>
    <hero/>

    <!-- Temp -->
    <article class="scrollTo" style="height: 2000px"></article>
  </main>
</template>

<script>
import Hero from './components/template-parts/Hero'
import ControlPanel from './components/ControlPanel'

export default {
  name: 'App',
  components: {ControlPanel, Hero},
  data: () => {
    return {isDark: true}
  },
  methods: {
    setTheme(dark) {
      this.isDark = dark;
    }
  },
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700;900&display=swap');

:root {
  --color-dark: #1C1D25;
  --color-dark-lighter: #393b4c;
  --color-light: #dbdbdb;
  --color-lightest: #FFF;
  --color-button-text: #FFF;
  --color-primary: #41B883;
  --color-secondary: #B84176;

  --base-transition-timing: .4s;
  --base-transition-motion: ease;
}

::selection {
  background: var(--color-dark-lighter);
  color: var(--color-light);
  text-shadow: none;
}

body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

* {
  font-family: 'Lato', sans-serif;
}

.light {
  --color-light: #323d4d;
  --color-lightest: #323d4d;
  --color-dark: #d7d7d7;
  --color-dark-lighter: #FFF;
}

</style>