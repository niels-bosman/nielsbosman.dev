<template>
  <main :class="[isDark ? 'dark' : 'light']">
    <control-panel :is-dark="isDark" @switch="isDark = !isDark"/>
    <hero/>

    <!-- Temp -->
    <article class="scrollTo" style="height: 2000px"></article>
  </main>
</template>

<script>
import Hero from './components/template-parts/Hero'
import ControlPanel from './components/atoms/ControlPanel'

export default {
  name: 'App',
  components: { ControlPanel, Hero },
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

<style>
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700;900&display=swap');

:root {
  --color-dark: #1C1D25;
  --color-dark-lighter: #393B4C;
  --color-light: #DBDBDB;
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
}

body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  -webkit-font-smoothing: subpixel-antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h1, h2, h3, h4, h5, h6 {
  font-family: 'Lato Black', sans-serif;
}

* {
  font-family: 'Lato', sans-serif;
}

.light {
  --color-light: #323D4D;
  --color-lightest: #323D4D;
  --color-dark: #E4E4E4;
  --color-dark-lighter: #FFF;
}
</style>