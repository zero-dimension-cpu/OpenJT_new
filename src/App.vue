<script>
import MyCarousel from './components/MyCarousel.vue'
export default {
  name: 'App',
  components: {
    MyCarousel
  }
}
</script>

<template>
 <div id="app">
  <MyCarousel />
 </div>
</template>

<style>
@font-face {
  font-family: 'iconfont';
  src: url('../font/iconfont.woff2?t=1729129233494') format('woff2'),
    url('../font/iconfont.woff?t=1729129233494') format('woff'),
    url('../font/iconfont.ttf?t=1729129233494') format('truetype');
}

.iconfont {
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.w {
  width: 100%;
  margin: 0 auto;
}
</style>
