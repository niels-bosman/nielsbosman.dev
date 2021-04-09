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
import Semicolon from './Semicolon'
import DoubleAnd from './DoubleAnd'
import ScrollButton from './ScrollButton'

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

$gutter: 20px;

.hero {
  position: relative;
  display: grid;
  place-items: center;
  height: calc(100vh - #{$gutter * 2});
  background: #2a2a2f;
  margin: $gutter;
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