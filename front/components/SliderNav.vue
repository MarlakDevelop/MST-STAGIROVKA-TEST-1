<template>
  <div class="sliderNav h-full flex flex-col justify-center">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style>
  .sliderNav {
    width: 280px;
    background-color: #FFFFFF;
  }
</style>
