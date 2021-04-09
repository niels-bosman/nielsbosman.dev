<template>
  <div class="hero">
    <article>
      <p>Hoi 👋, ik ben</p>
      <h1>
        Niels Bosman<semicolon/>
      </h1>
      <p class="subtitle">
        Webontwikkelaar
        <double-and/>
        student
      </p>
    </article>
    <scroll-button/>
  </div>
</template>

<script>
import Semicolon from '../helpers/Semicolon'
import DoubleAnd from '../helpers/DoubleAnd'
import ScrollButton from '../buttons/ScrollButton'

export default {
  name: 'Hero',
  components: {
    Semicolon,
    DoubleAnd,
    ScrollButton
  }
}
</script>

<style lang="scss" scoped>

.hero {
  position: relative;
  display: grid;
  place-items: center;
  height: 100vh;
  background: url("../../assets/background-hero.svg") fixed;
  background-size: cover;

  &:after {
    content: '';
    background-color: black;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    opacity: 40%;
  }
}

article {
  z-index: 1;
}

h1 {
  font-weight: 900;
  font-size: 10em;
  margin: 20px 0;
  color: #fff;
}

p {
  font-weight: 500;
  font-size: 30px;
  color: #c1c1c1;
}

.subtitle {
  text-align: right;
  font-weight: 500;
}

</style>