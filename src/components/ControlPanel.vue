<template>
  <aside class="control-panel">
    <ul class="list">
      <li class="item" :class="{'active' : isDark}" @click="setDark">
        <i class="fas fa-moon" />
      </li>
      <li class="item" :class="{'active' : !isDark}" @click="setLight">
        <i class="fas fa-sun" />
      </li>
    </ul>
  </aside>
</template>

<script>
export default {
  name: 'ControlPanel',
  data() {
    return {
      isDark: true
    }
  },
  methods: {
    change(dark) {
      if (this.isDark !== dark) {
        this.isDark = dark
        this.$emit("switch", this.isDark)
      }
    },
    setDark() {
      this.change(true)
    },
    setLight() {
      this.change(false)
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
  background: var(--color-dark-lighter);
  z-index: 1;
  transition: var(--base-transition-timing) var(--base-transition-motion) background;
  will-change: background;
}

.list {
  padding: 0;
  margin: 0;
  list-style: none;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.item {
  font-size: 26px;
  color: var(--color-lightest);
  padding: 20px 16px;
  border-radius: 0;
  cursor: pointer;
  transition: var(--base-transition-timing) var(--base-transition-motion) all;
  will-change: transform, border-radius, color, background, box-shadow;

  &:hover {
    transform: scale(.9);
  }

  &.active {
    border-radius: 24px;
    box-shadow: 0 0 20px -10px rgba(0,0,0,0.4);

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