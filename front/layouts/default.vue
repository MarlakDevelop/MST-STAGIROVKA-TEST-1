<template>
  <div>
    <Header>
      <template v-slot:title>
        {{ title }}
      </template>
      <NavBar :links="links"></NavBar>
      <template v-slot:phone>
        {{ phone }}
      </template>
    </Header>
    <div class="pageContainer">
      <Nuxt />
    </div>
    <Footer>{{ footer }}</Footer>
  </div>
</template>

<script type="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      title: 'Первомайская',
      phone: '8 888 888 88 88',
      links: [
        {
          name: 'О комплексе',
          to: '/'
        },
        {
          name: 'Особенности',
          to: '/features'
        },
        {
          name: 'Пентхаусы',
          to: '/houses'
        },
        {
          name: 'Выбрать квартиру',
          to: '/floors'
        }
      ],
      footer: 'Разработано в MST      |      2018'
    }
  }
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

@font-face {
  font-family: Gilroy;
  src: url(/fonts/Gilroy-ExtraBold.otf);
}

@font-face {
  font-family: Gilroy;
  src: url(/fonts/Gilroy-Light.otf);
}

.sideBlock {
  height: 60px;
}

.pageContainer {
  height: calc(100vh - 120px);
  background-color: #F0F0F0;
  border-left: 60px solid #FFFFFF;
  border-right: 60px solid #FFFFFF;
}

.page-enter-active,
.page-leave-active {
  transition: opacity 0.4s;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}

.layout-enter-active,
.layout-leave-active {
  transition: opacity 0.4s;
}
.layout-enter,
.layout-leave-to {
  opacity: 0;
}

</style>
