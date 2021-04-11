<template>
  <ul class="list">
    <li class="item">
      <a href="https://github.com/niels-bosman" target="_blank" title="Github">
        <i class="fab fa-github"></i>
      </a>
    </li>
    <li class="item">
      <a href="https://www.linkedin.com/in/nielz" target="_blank" title="LinkedIn">
        <i class="fab fa-linkedin"></i>
      </a>
    </li>
    <li class="item">
      <a href="https://stackoverflow.com/users/12377207/niels-bosman" target="_blank" title="Stack Overflow">
        <i class="fab fa-stack-overflow"></i>
      </a>
    </li>
    <li class="item"></li>
  </ul>
</template>

<script>
export default {
  name: 'Socials'
}
</script>

<style scoped lang="scss">

@import "../../assets/scss/mixins";

.list {
  position: absolute;
  left: 15px;
  top: 15px;
  list-style: none;
  display: flex;
  padding: 0;
  margin: 0;
}

.item {
  transition: var(--base-transition-timing) var(--base-transition-motion) transform;
  will-change: transform;

  &:hover {
    transform: translateY(3px);
  }

  a {
    @include fluidFontSize(1.5em, 2em);
    color: var(--color-light);
    font-size: 2em;
    margin-right: 20px;
    transition: var(--base-transition-timing) var(--base-transition-motion) color;
    will-change: color;

    @media (max-width: 600px) {
      margin-right: 10px;
    }

    &:hover {
      transform: scale(.9);
      color: var(--color-lightest);
    }
  }


  &:last-child a {
    margin-right: 0;
  }
}

</style>