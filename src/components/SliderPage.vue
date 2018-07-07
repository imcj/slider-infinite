<template>
    <div class="slider-item">
        <!-- <div>{{source}}</div> -->
        <image class="image" resize="cover" :src="source"></image>
    </div>
</template>
<script>
export default {
  name: 'SliderPage',
  components: {
  },
  props: {
      source: {
          type: String,
          default: ""
      }
  },
  data () {
    return {
    }
  }
}
</script>
<style scoped>
    .slider-item {
        font-size: 80px;
    }

    .image {
        width: 700px;
        height: 700px;
    }
</style>
