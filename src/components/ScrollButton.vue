<template>
  <a href="#">Meer over mij &nbsp;&nbsp;<i class="fas fa-level-down-alt"></i></a>
</template>

<script>
export default {
  name: "ScrollButton"
}
</script>

<style lang="scss" scoped>
a {
  text-transform: uppercase;
  color: white;
  background-color: #41B883;
  border-radius: 24px;
  text-decoration: none;
  padding: 16px 32px;
  font-weight: 700;
  font-size: 15px;
  transition: .2s ease background-color;
  will-change: background-color;

  &:hover {
    background-color: lighten(#41B883, 10%);
  }
}
</style>