<template>
  <div class="button-wrapper">
    <base-button title="Meer over mij" @click="scroll">
      Meer over mij&nbsp;&nbsp;<i class="fas fa-level-down-alt"/>
    </base-button>
  </div>
</template>

<script>
import BaseButton from './BaseButton'

export default {
  name: 'ScrollButton',
  components: { BaseButton },
  methods: {
    scroll() {
      document.querySelector('.about-me').scrollIntoView({ behavior: 'smooth' })
    }
  }
}
</script>

<style lang="scss" scoped>
.button-wrapper {
  position: absolute;
  right: 50%;
  bottom: 80px;
  transition: .3s ease all;
  will-change: transform;
  z-index: 1;
  transform: translate(50%, 0);

  @media (max-width: 900px) {
    bottom: 20px;
  }

  &:hover {
    transform: translate(50%, -5px);
  }
}
</style>