<template>
  <ul class="list">
    <li class="item">
      <a :href="urls.github"
         target="_blank"
         title="GitHub"
         rel="nofollow"
      >
        <i class="fab fa-github"/>
      </a>
    </li>A
    <li class="item">
      <a :href="urls.linkedin"
         target="_blank"
         rel="nofollow"
         title="LinkedIn"
      >
        <i class="fab fa-linkedin"/>
      </a>
    </li>
    <li class="item">
      <a :href="urls.instagram"
         target="_blank"
         rel="nofollow"
         title="Instagram"
      >
        <i class="fab fa-instagram"/>
      </a>
    </li>
    <li class="item">
      <a :href="`mailto:${urls.email}`"
         rel="nofollow"
         title="Email"
      >
        <i class="far fa-envelope-open"/>
      </a>
    </li>

  </ul>
</template>

<script>
export default {
  name: 'Socials',
  data() {
    return {
      urls: {
        github: "https://github.com/niels-bosman",
        linkedin: "https://www.linkedin.com/in/nielz",
        instagram: "https://instagram.com/nielsrbosman",
        email: "nielsbosman@mail.com",
      }
    }
  },
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