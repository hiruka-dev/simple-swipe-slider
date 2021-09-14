<template>
  <div id="app">
    <SimpleSwipeSlider :images="images"/>
  </div>
</template>

<script>
import SimpleSwipeSlider from './components/SimpleSwipeSlider.vue'

export default {
  name: 'App',
  data () {
    return {
      images: [
        "https://image.uniqlo.com/UQ/ST3/AsianCommon/imagesgoods/441600/item/goods_02_441600.jpg?width=400",
        "https://image.uniqlo.com/UQ/ST3/AsianCommon/imagesgoods/441600/item/goods_12_441600.jpg?width=400",
        "https://image.uniqlo.com/UQ/ST3/AsianCommon/imagesgoods/441600/item/goods_39_441600.jpg?width=400",
        "https://image.uniqlo.com/UQ/ST3/AsianCommon/imagesgoods/441600/item/goods_47_441600.jpg?width=400"
      ]
    }
  },
  components: {
    SimpleSwipeSlider
  }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
