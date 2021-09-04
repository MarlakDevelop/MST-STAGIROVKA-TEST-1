<template>
  <div class="header sideBlock flex justify-between relative items-center">
    <div class="cubeContainer left">
      <div class="cube"></div>
    </div>
    <div class="title">
      <slot name="title"></slot>
    </div>
    <slot></slot>
    <div class="phone">
      <slot name="phone"></slot>
    </div>
    <div class="cubeContainer right">
      <div class="cube">
        <svg width="29" height="29" viewBox="0 0 29 29" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd" clip-rule="evenodd" d="M0.998047 26.5521L26.5556 0.994995L28.005 2.44425L2.44665 28.0015L0.998047 26.5521ZM12.9987 26.5521L26.5556 12.9956L28.005 14.4435L14.4474 28.0015L12.9987 26.5521ZM14.5569 0.994995L0.998047 14.5532L2.44665 16.0009L16.0042 2.44425L14.5569 0.994995Z" fill="#F0F0F0"/>
        </svg>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style>
  .header {
    padding: 0 120px;
  }

  .header .title, .header .phone {
    font-family: Gilroy;
    font-style: normal;
    font-weight: bold;
    font-size: 17px;
    line-height: 21px;
    letter-spacing: 0.290629px;
    text-transform: uppercase;
    color: #262525;
    margin-top: 5px;
  }

  .cubeContainer {
    position: absolute;
    top: 25px;
    height: 70px;
    width: 70px;
    background-color: #262525;
    z-index: 1000;
  }

  .cubeContainer.left {
    left: 25px;
  }

  .cubeContainer.right {
    right: 25px;
  }

  .cube {
    position: relative;
    height: 100%;
    width: 100%;
  }

  .cube svg {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>
