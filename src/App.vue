<template>
  <hero />
</template>

<script>
import Hero from "./components/Hero";

export default {
  name: 'App',
  components: {
    Hero
  }
}
</script>

<style>

body {
  margin: 0;
  padding: 0;
}

@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700;900&display=swap');

h1, h2, h3, h4, h5, h6, p, a {
  font-family: 'Lato', sans-serif;
}
</style>