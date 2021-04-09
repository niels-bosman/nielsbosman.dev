<template>
  <div class="button-wrapper">
    <a class="button" href="#" title="Meer over mij">Meer over mij &nbsp;&nbsp;<i class="fas fa-level-down-alt"></i></a>
  </div>
</template>

<script>
export default {
  name: "ScrollButton"
}
</script>

<style lang="scss" scoped>

.button-wrapper {
  position: absolute;
  right: 50%;
  bottom: 80px;
  transition: .3s ease all;
  will-change: transform;

  &:hover {
    transform: translateY(-5px);

    .button {
      background-color: lighten(#41B883, 5%);
      border-radius: 5px;
    }
  }
}

.button {
  border: none;
  text-transform: uppercase;
  color: white;
  background-color: #41B883;
  border-radius: 24px;
  text-decoration: none;
  padding: 16px 32px;
  font-weight: 700;
  font-size: 15px;
  transition: .2s ease all;
  will-change: background-color;
}
</style>