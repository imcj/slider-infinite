<template>
  <div>
    <slider-infinite v-bind:pages="imageList">
      <template slot-scope="props">
          <slider-page :page="props.page" :index="props.index" :slider-index="props.sliderIndex">
          </slider-page>
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
          { src: 'https://ikeep.oss-cn-hangzhou.aliyuncs.com/tips/text-1.png', index: 0},
          { src: 'https://ikeep.oss-cn-hangzhou.aliyuncs.com/tips/text-2.png', index: 1},
          { src: 'https://ikeep.oss-cn-hangzhou.aliyuncs.com/tips/text-3.png', index: 2},
          { src: 'https://ikeep.oss-cn-hangzhou.aliyuncs.com/tips/text-4.png', index: 3},
          { src: 'https://ikeep.oss-cn-hangzhou.aliyuncs.com/tips/text-5.png', index: 4},
          { src: 'https://ikeep.oss-cn-hangzhou.aliyuncs.com/tips/text-6.png', index: 5}
        ]
      }
  },

  created() {
    console.debug("index.vue created")
  }
}
</script>

<style scoped>
  .image {
    width: 700px;
    height: 700px;
  }

  .web {
    width: 700px;
    height: 700px;
  }

</style>
