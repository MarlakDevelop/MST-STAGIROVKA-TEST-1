<template>
  <div
    ref="navBar"
    class="navBar h-full flex justify-between items-center relative"
  >
    <NavLink
      v-for="link in links"
      :to="link.to"
      @selected="itemSelected"
      @hover="itemHovered"
      @clearhover="itemClearHover"
    >
      {{ link.name }}
    </NavLink>
    <hr
      ref="navBarLine"
      class="absolute"
      style="left: 0; right: 100%;"
    />
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  props: ['links'],
  data() {
    return {
      slideOptions: {
        selectedRef: null,
        hoveredRef: null
      }
    }
  },
  methods: {
    itemSelected(reference) {
      this.slideOptions.selectedRef = reference;
      const fromLeftPX = this.slideOptions.selectedRef.$el.offsetLeft - 4;
      const fromRightPX = this.$refs.navBar.offsetWidth - (this.slideOptions.selectedRef.$el.offsetWidth + fromLeftPX + 8);
      this.$refs.navBarLine.style.left = `${fromLeftPX}px`;
      this.$refs.navBarLine.style.right = `${fromRightPX}px`;
    },
    itemHovered(reference) {
      this.slideOptions.hoveredRef = reference;
      let fromLeftPX = this.slideOptions.hoveredRef.$el.offsetLeft - 4;
      let fromRightPX;
      if (fromLeftPX > this.slideOptions.selectedRef.$el.offsetLeft) {
        fromRightPX = this.$refs.navBar.offsetWidth - (this.slideOptions.hoveredRef.$el.offsetWidth + fromLeftPX + 8);
        fromLeftPX = this.slideOptions.selectedRef.$el.offsetLeft - 4;
      } else {
        fromLeftPX = this.slideOptions.selectedRef.$el.offsetLeft - 4;
        fromRightPX = this.$refs.navBar.offsetWidth - (this.slideOptions.selectedRef.$el.offsetWidth + fromLeftPX + 8);
        fromLeftPX = this.slideOptions.hoveredRef.$el.offsetLeft - 4;
      }
      this.$refs.navBarLine.style.left = `${fromLeftPX}px`;
      this.$refs.navBarLine.style.right = `${fromRightPX}px`;
    },
    itemClearHover() {
      this.slideOptions.hoveredRef = null;
      const fromLeftPX = this.slideOptions.selectedRef.$el.offsetLeft - 4;
      const fromRightPX = this.$refs.navBar.offsetWidth - (this.slideOptions.selectedRef.$el.offsetWidth + fromLeftPX + 8);
      this.$refs.navBarLine.style.left = `${fromLeftPX}px`;
      this.$refs.navBarLine.style.right = `${fromRightPX}px`;
    }
  }
})
</script>

<style>
  .navBar {
    width: 500px;
  }

  .navBar hr {
    height: 4px;
    bottom: 12px;
    transition: all 0.4s;
    background-color: #D88F5E;
  }
</style>
