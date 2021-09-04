<template>
  <div class="sliderNavItemContainer">
    <a
      :class="`sliderNavItem ${active ? 'active' : ''}`"
      @click="$emit('clicked', $event.target.value)"
    >
      <b>
        <slot></slot>
      </b>
    </a>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: ['active']
})
</script>

<style>
  .sliderNavItemContainer {
    height: 20px;
    margin-top: 15px;
    margin-bottom: 15px;
  }

  .sliderNavItem {
    font-family: Roboto;
    font-style: normal;
    font-weight: 300;
    font-size: 13px;
    line-height: 15px;
    letter-spacing: 0.567739px;
    color: #505050;
    cursor: pointer;
    transition: all 0.4s;
    position: relative;
  }

  .sliderNavItem b {
    position: relative;
    z-index: 10;
  }

  .sliderNavItem::after {
    content: "";
    background-color: transparent;
    height: 9px;
    transition: all 0.4s;
    position: absolute;
    left: -4px;
    right: -4px;
    bottom: -4px;
    z-index: 0;
  }

  .sliderNavItem:hover {
    color: #262525;
  }

  .sliderNavItem:hover::after {
    background-color: #EBD8CC;
  }

  .sliderNavItem.active {
    font-weight: bold;
    font-size: 14px;
    line-height: 16px;
    text-transform: uppercase;
    color: #262525;
  }

  .sliderNavItem.active::after {
    background-color: #EBD8CC;
  }

</style>

