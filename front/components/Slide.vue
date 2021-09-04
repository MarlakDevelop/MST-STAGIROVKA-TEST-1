<template>
  <div
    :class="'slideContainer absolute top-0 left-0 right-0 bottom-0' + slide.classes"
  >
    <div class="slide h-full w-full">
      <div class="slideMeta metaContainer">
        <div class="title">{{ slide.title }}</div>
        <div class="description">{{ slide.description }} <a class="moreButton"><svg width="12" height="3" viewBox="0 0 12 3" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd" clip-rule="evenodd" d="M0.5 0.5H2.73948V2.74064H0.5V0.5ZM4.98031 0.500004H7.21969V2.74064H4.98031V0.500004ZM11.7001 0.500004H9.45919V2.74064H11.7001V0.500004Z" fill="white"/>
        </svg></a></div>
      </div>
      <div class="slideImageContainer overflow-hidden">
        <img
          :src="slide.imageSrc"
          class="slideImage"
        ></img>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: ['slide']
})
</script>

<style>
  .slideContainer {
    position: absolute;
    visibility: hidden;
  }

  .slideContainer.active, .slideContainer.prevSlideDisappear, .slideContainer.nextSlideDisappear {
    visibility: visible;
  }

  .slideContainer .slide .slideMeta {
    color: #262525;
    left: 10%;
    top: 50%;
    opacity: 1;
    transform: translate(0, -50%);
    transition: top 0.6s, opacity 0.6s;
  }

  .slideContainer .slide .title {
    font-family: Gilroy;
    font-style: normal;
    font-weight: bold;
    font-size: 44px;
    line-height: 53px;
    letter-spacing: -0.0255199px;
    text-transform: uppercase;
  }

  .slideContainer .slide .description {
    font-family: Roboto;
    font-style: normal;
    font-weight: normal;
    font-size: 18px;
    line-height: 30px;
    letter-spacing: -0.0220791px;
    margin-top: 40px;
  }

  .slideContainer .slide .slideImageContainer, .slideContainer .slide .slideImageContainer .slideImage {
    @apply block absolute top-0 right-0 bottom-0;
    width: 770px;
  }

  .slideContainer .slide .moreButton {
    display: inline-block;
    height: 28px;
    width: 28px;
    background-color: #262525;
    position: relative;
    cursor: pointer;
    vertical-align: middle;
    margin-left: 6px;
  }

  .slideContainer .slide .moreButton svg {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  .slideContainer.appearFromPrev .slide .slideMeta {
    animation-name: slideMetaAppearFromPrev;
    animation-duration: 0.4s;
    animation-timing-function: linear;
    animation-iteration-count: 1;
    animation-direction: alternate;
    animation-delay: 0s;
    animation-fill-mode: forwards;
  }

  .slideContainer.appearFromPrev .slide .slideImageContainer {
    animation-name: slideImageAppearFromPrev;
    animation-duration: 0.4s;
    animation-timing-function: linear;
    animation-iteration-count: 1;
    animation-direction: alternate;
    animation-delay: 0s;
    animation-fill-mode: forwards;
  }

  .slideContainer.appearFromNext .slide .slideMeta {
    animation-name: slideMetaAppearFromNext;
    animation-duration: 0.4s;
    animation-timing-function: linear;
    animation-iteration-count: 1;
    animation-direction: alternate;
    animation-delay: 0s;
    animation-fill-mode: forwards;
  }

  .slideContainer.appearFromNext .slide .slideImageContainer {
    animation-name: slideImageAppearFromNext;
    animation-duration: 0.4s;
    animation-timing-function: linear;
    animation-iteration-count: 1;
    animation-direction: alternate;
    animation-delay: 0s;
    animation-fill-mode: forwards;
  }

  .slideContainer.prevSlideDisappear .slide .slideImageContainer {
    animation-name: prevSlideImageDisappear;
    animation-duration: 0.4s;
    animation-timing-function: linear;
    animation-iteration-count: 1;
    animation-direction: alternate;
    animation-delay: 0s;
    animation-fill-mode: forwards;
  }

  .slideContainer.nextSlideDisappear .slide .slideImageContainer {
    animation-name: nextSlideImageDisappear;
    animation-duration: 0.4s;
    animation-timing-function: linear;
    animation-iteration-count: 1;
    animation-direction: alternate;
    animation-delay: 0s;
    animation-fill-mode: forwards;
  }

  .slideContainer.prevSlideDisappear .slide .slideMeta, .slideContainer.nextSlideDisappear .slide .slideMeta {
    animation-name: slideMetaDisappear;
    animation-duration: 0.4s;
    animation-timing-function: linear;
    animation-iteration-count: 1;
    animation-direction: alternate;
    animation-delay: 0s;
    animation-fill-mode: forwards;
  }

  @keyframes slideMetaAppearFromPrev {
    0% {
      top: 60%;
      opacity: 0;
    }
    100% {
      top: 50%;
      opacity: 1;
    }
  }

  @keyframes slideImageAppearFromPrev {
    0% {
      bottom: 100%;
    }
    100% {
      bottom: 0;
    }
  }

  @keyframes slideMetaAppearFromNext {
    0% {
      top: 40%;
      opacity: 0;
    }
    100% {
      top: 50%;
      opacity: 1;
    }
  }

  @keyframes slideImageAppearFromNext {
    0% {
      opacity: 0;
    }
    1% {
      opacity: 1;
    }
    100% {
      opacity: 1;
    }
  }

  @keyframes nextSlideImageDisappear {
    0% {
      bottom: 0;
    }
    100% {
      bottom: 100%;
    }
  }

  @keyframes prevSlideImageDisappear {
    0% {
      opacity: 1;
    }
    99% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }

  @keyframes slideMetaDisappear {
    0% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }
</style>
