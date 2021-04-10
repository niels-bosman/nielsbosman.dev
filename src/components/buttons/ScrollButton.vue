<template>
  <base-button title="Meer over mij" @click="scroll">
    Meer over mij&nbsp;&nbsp;<i class="fas fa-level-down-alt"></i>
  </base-button>
</template>
<script>

import BaseButton from './BaseButton'

export default {
  name: 'ScrollButton',

  components: {BaseButton},

  methods: {
    scroll() {
      document.querySelector('.scrollTo').scrollIntoView({behavior: 'smooth'})
    }
  }
}

</script>