<template>
  <div>
    <!-- <slider class="slider" interval="3000" infinite="false" auto-play="false">
      <div class="frame" v-for="img in imageList">
        <image class="image" resize="cover" :src="img.src"></image>
      </div>
    </slider> -->
    <!-- <image class="image" resize="cover" :src="img.src"></image> -->
    <slider-infinite v-bind:pages="imageList">
      <template slot-scope="props">
        <slider-page :source="props.source"></slider-page>
         <!-- <span class="slider-item">{{ props.source }} 123 {{props}}</span> -->
       </template>
      
    </slider-infinite>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
    "slider-infinite": require("./components/SliderInfinite"),
    'slider-page': require("./components/SliderPage")
  },
  data () {
    return {
        imageList: [
          { src: 'http://127.0.0.1:3000/text-1.png', index: 0},
          { src: 'http://127.0.0.1:3000/text-2.png', index: 1},
          { src: 'http://127.0.0.1:3000/text-3.png', index: 2},
          { src: 'http://127.0.0.1:3000/text-4.png', index: 3},
          { src: 'http://127.0.0.1:3000/text-5.png', index: 4},
          { src: 'http://127.0.0.1:3000/text-6.png', index: 5}
        ]
      }
  }
}
</script>

<style scoped>
  .image {
    width: 700px;
    height: 700px;
  }

  .slider-item {
    font-size: 80px;
  }

  slider-infinite {
    margin-top: 25px;
    margin-left: 25px;
    width: 700px;
    height: 700px;
    border-width: 2px;
    border-style: solid;
    border-color: #41B883;
  }
  .frame {
    width: 700px;
    height: 700px;
    position: relative;
  }
</style>
