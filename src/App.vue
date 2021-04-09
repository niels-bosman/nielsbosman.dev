<template>
  <hero />
  <article class="main">
    Main
  </article>
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

body {
  margin: 0;
  padding: 0;
}

h1, h2, h3, h4, h5, h6, p, a, button {
  font-family: 'Lato', sans-serif;
}

</style>