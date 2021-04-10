<template>
  <aside class="control-panel">
    <ul class="list">
      <li class="item" :class="{'active' : isDark}" @click="change(true)">
        <i class="fas fa-moon" />
      </li>
      <li class="item" :class="{'active' : !isDark}" @click="change(false)">
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
}

.list {
  padding: 0;
  margin: 0;
  list-style: none;
  display: flex;
  flex-direction: column;
}

.item {
  font-size: 26px;
  color: var(--color-lightest);
  padding: 20px 16px;
  cursor: pointer;
  transition: var(--base-transition-timing) var(--base-transition-motion) color, background;

  &.active {
    color: var(--color-primary);

    &:first-child {
      border-radius: 24px 24px 0 0;
      background: #ffffff08;
    }

    &:last-child {
      border-radius: 0 0 24px 24px;
      background: #00000008;
    }
  }
}

</style>