<template>
  <div class="wrapper">
    <article>
      <p>Hoi 👋, ik ben</p>
      <h1>Niels Bosman<semicolon /></h1>
    </article>
  </div>
</template>

<script>
import Semicolon from './semicolon'

export default {
  name: 'Hero',
  components: {
    Semicolon
  }
}
</script>

<style lang="scss" scoped>

$gutter: 15px;

.wrapper {
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
  font-weight: 700;
  font-size: 30px;
  color: #c1c1c1;
}
</style>