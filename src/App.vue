<template>
  <hero />
  <article class="main" style="height: 2000px"></article>
</template>

<script>
import Hero from './components/template-parts/Hero'

export default {
  name: 'App',
  components: {
    Hero
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700;900&display=swap');

:root {
  --color-dark: #1C1D25;
  --color-light: #d7d7d7;
  --color-lightest: #FFF;
  --color-primary: #41B883;
  --color-secondary: #B84176;
}

body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

* {
  font-family: 'Lato', sans-serif;
}

</style>