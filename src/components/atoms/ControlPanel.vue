<template>
  <aside class="control-panel">
    <ul class="list">
      <li class="item" :class="{'active' : isDark}" @click="change(true)">
        <i class="fas fa-moon"/>
      </li>
      <li class="item" :class="{'active' : !isDark}" @click="change(false)">
        <i class="fas fa-sun"/>
      </li>
    </ul>
  </aside>
</template>

<script>
export default {
  name: 'ControlPanel',
  props: {
    isDark: { type: Boolean, required: true },
  },
  methods: {
    change(wantsToBeDark) {
      // We only want to switch the theme if it is not equal to the current theme.
      if (wantsToBeDark !== this.isDark) {
        this.$emit("switch")
        window.localStorage.setItem('theme', wantsToBeDark ? 'dark' : 'light')
      }
    }
  },
}
</script>

<style scoped lang="scss">
.control-panel {
  position: fixed;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  border-radius: 24px;
  background: var(--color-dark-light);
  z-index: 99;
  transition: var(--base-transition-timing) var(--base-transition-motion) background;
  will-change: background;

  @media (max-width: 900px) {
    top: 20px;
    transform: translate(0, 0);
  }
}

.list {
  padding: 0;
  margin: 0;
  list-style: none;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  border-radius: 24px;
}

.item {
  font-size: 26px;
  color: var(--color-lightest);
  padding: 20px 16px;
  border-radius: 0;
  cursor: pointer;
  transition: var(--base-transition-timing) var(--base-transition-motion) all;
  will-change: transform, border-radius, color, background, box-shadow;

  @media (max-width: 600px) {
    padding: 15px 12px;
  }

  &:hover:not(.active) {
    transform: scale(.9);
  }

  &.active {
    border-radius: 24px;
    box-shadow: 0 0 20px -10px rgba(0, 0, 0, 0.4);

    &:first-child {
      color: #F5F3CE;
      background: #ffffff08;
    }

    &:last-child {
      color: #F28C38;
    }
  }
}
</style>