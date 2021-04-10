<template>
  <main
      :class="isDark ? 'dark' : 'light'"
      @click="isDark = !isDark"
  >
    <hero/>
    <article style="height: 2000px"></article>
  </main>
</template>

<script>
import Hero from './components/template-parts/Hero'

export default {
  name: 'App',
  components: {Hero},
  data: () => {
    return {isDark: true}
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700;900&display=swap');

:root {
  --color-dark: #1C1D25;
  --color-light: #d7d7d7;
  --color-lightest: #FFF;
  --color-button-text: #FFF;
  --color-primary: #41B883;
  --color-secondary: #B84176;
  --base-transition-timing: .4s;
  --base-transition-motion: ease;
}

body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

* {
  font-family: 'Lato', sans-serif;
}

.light {
  --color-light: #323d4d;
  --color-lightest: #323d4d;
  --color-dark: #d7d7d7;
}

</style>