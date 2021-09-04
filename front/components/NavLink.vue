<template>
  <NuxtLink
    ref="link"
    :to="to"
    @click.native="select"
    @mouseover.native="hover"
    @mouseout.native="clearHover"
    class="navLink">
    <slot></slot>
  </NuxtLink>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: ['to'],
  mounted() {
    if (this.$route.path == this.to) {
      this.select()
    }
  },
  methods: {
    select(): void {
      this.$emit('selected', this.$refs['link']);
    },
    hover(): void {
      this.$emit('hover', this.$refs['link']);
    },
    clearHover(): void {
      this.$emit('clearhover');
    }
  }
})
</script>

<style scoped>
  .navLink {
    font-family: Gilroy;
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 15px;
    letter-spacing: 0.8px;
    text-transform: uppercase;
    color: #262525;
  }
</style>
