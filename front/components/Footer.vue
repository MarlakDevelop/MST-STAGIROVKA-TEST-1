<template>
  <div class="footer sideBlock flex justify-between items-center">
    <pre><slot></slot></pre>
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({})
</script>

<style>
  .footer {
    font-family: Gilroy;
    font-style: normal;
    font-weight: 300;
    font-size: 13px;
    line-height: 15px;
    letter-spacing: 0.175729px;
    text-transform: uppercase;
    color: #505050;
    padding: 0 60px;
  }
</style>
