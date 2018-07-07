<template>
    <slider class="slider" interval="3000" infinite="false" auto-play="false" @change="onChange" :index="index">
        <slot v-for="(page, i) in limitPages" :page="page" :index="i" :slider-index="index">
        </slot>
    </slider>
</template>

<script>

export default {
    components: {
    },

    props: {
        pages: {
            type: Array,
            default: []
        },
    },

    data() {
        return {
            limitPages: [],
            index: 0,
        }
    },

    created() {
        this.limitPages = this.pages
        this.index = 0
    },

    methods: {
        onChange(event) {
            this.index = event.index
        }
    }
}
</script>


<style scoped>
    .slider {
        width: 100%;
        height: 700px;
    }
</style>