<template>
  <div class="h-full flex">
    <SliderNav>
      <SliderNavItem
        v-for="slide in slides"
        :active="slide.active"
        @clicked="setSlide(slide.id)"
      >
        {{ slide.title }}
      </SliderNavItem>
    </SliderNav>
    <div
      class="sliderContainer h-full w-full flex-1 relative"
    >
      <Slide
        v-for="slide in slides"
        :slide="slide"
      ></Slide>
      <div class="pageCounter flex metaContainer">
        <div class="pageCounterItem primal">
          {{ currentPage }}
        </div>
        <div class="pageCounterItem">
          /
        </div>
        <div class="pageCounterItem">
          {{ pagesTotal }}
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export interface SlideModel {
  id: number,
  title: string,
  description: string,
  imageSrc: string,
  active: boolean,
  classes: string
}

export default Vue.extend({
  data() {
    return {
      slides: [
        {
          id: 1,
          title: 'Архитектура',
          description: 'Оригинальная архитектура жилого комплекса бизнес-класса «Первомайская» формирует современный стиль жизни',
          imageSrc: '/images/main-slider/1.png',
          active: true,
          classes: ' active'
        },
        {
          id: 2,
          title: 'Благоустройство',
          description: 'Запроектированные большие окна, которые пропускают много солнечного света, наполнят Ваши квартиры теплотой и уютом',
          imageSrc: '/images/main-slider/2.png',
          active: false,
          classes: ''
        },
        {
          id: 3,
          title: 'Безопасность',
          description: 'Современный двор европейского уровня — территория для детей, игр на свежем воздухе и вечерних',
          imageSrc: '/images/main-slider/3.png',
          active: false,
          classes: ''
        },
        {
          id: 4,
          title: 'Инженерия',
          description: 'Оригинальная архитектура жилого комплекса бизнес-класса «Первомайская» формирует современный стиль жизни',
          imageSrc: '/images/main-slider/4.png',
          active: false,
          classes: ''
        },
        {
          id: 5,
          title: 'Инфраструктура',
          description: 'Прекрасный вариант для тех, кто предпочитает жить в спокойном районе среди интеллигенции, но при этом чувствовать ритм мегаполиса',
          imageSrc: '/images/main-slider/5.png',
          active: false,
          classes: ''
        },
        {
          id: 6,
          title: 'Транспортная доступность',
          description: 'Жилой комплекс «Первомайска» расположен в престижном Академическом районе',
          imageSrc: '/images/main-slider/6.png',
          active: false,
          classes: ''
        }
      ]
    }
  },
  computed: {
    pagesTotal(): number {
      return this.slides.length;
    },
    currentPage(): number {
      const currentSlide = this.slides.indexOf(this.slides.filter((slide: SlideModel): boolean => {
        return slide.active;
      })[0]);
      return currentSlide + 1;
    },
  },
  methods: {
    setSlide(slideId: number): void {
      if (slideId == this.slides.filter((slide: SlideModel): boolean => {
        return slide.active;
      })[0].id){
        return;
      }
      let currentSlideFlag = false;
      let beforeSlideFlag = false;
      this.slides = this.slides.map((slide: SlideModel): SlideModel => {
        slide.classes = '';
        if (slide.active && slideId != slide.id) {
          beforeSlideFlag = true
          slide.classes += currentSlideFlag ? ' nextSlideDisappear' : ' prevSlideDisappear'
          slide.active = false;
        }
        else if (slideId == slide.id) {
          currentSlideFlag = true
          slide.classes += ' active'
          slide.classes += beforeSlideFlag ? ' appearFromPrev' : ' appearFromNext'
          slide.active = (slideId == slide.id);
        }
        return slide;
      })
    }
  }
})
</script>

<style>
  .metaContainer {
    position: absolute;
    max-width: 435px;
  }

 .pageCounter {
   font-family: Gilroy;
   font-style: normal;
   font-weight: 300;
   font-size: 17px;
   line-height: 20px;
   text-align: center;
   color: #505050;
   left: 10%;
   bottom: 15%;
 }

 .pageCounter .pageCounterItem {
   @apply mx-0.5;
 }

 .pageCounter .pageCounterItem.primal {
   color: #262525;
 }
</style>
