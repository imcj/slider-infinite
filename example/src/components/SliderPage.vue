<template>
    <div>
        <image class="image" resize="cover" :src="page.src"  v-if="appear"></image>
    </div>
</template>
<script>
export default {
  name: 'SliderPage',
  components: {
  },
  props: {

      page: {
          type: Object,
          default: ""
      },

      appear: {
          type: Boolean,
          default: false
      },

      index: {
          type: Number,
          default: 0
      },

      sliderIndex: {
          type: Number,
          default: 0
      }
  },
  data () {
    return {
        initialized: false
    }
  },
  watch: {
      sliderIndex(value) {
          this.appear = true
          if (this.index == this.sliderIndex) {
              console.debug("SliderPage.vue sliderIndex " + value + " current page index is " + this.index + " " + Math.random())
              this.appear = true
          } else {
              if (this.appear == true) {
                this.appear = false
              }
          }
      }
  },

  methods: {

  },

  created() {
      if (0 == this.index) {
          this.appear = true
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