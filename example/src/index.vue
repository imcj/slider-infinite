<template>
  <div>
    <slider-infinite v-bind:pages="imageList">
      <template slot-scope="props">
        <div>
          <slider-page :page="props.page" :index="props.index" :slider-index="props.sliderIndex">
            <template slot-scope="props">
              <image class="image" resize="cover" :src="props.page.src"></image>
            </template>
          </slider-page>
        </div>
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
</style>
