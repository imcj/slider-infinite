<template>
    <div>
        <div v-for="(item, index) in items">{{item}}</div>
        <!--  :keep-index="keepIndex" -->
        <slider class="slider" interval="3000" infinite="false" auto-play="false" @change="onChange" :index="index">
            <!-- <div class="item" v-for="(item, index) in items">{{item}}</div> -->
            <slot v-for="(page) in limitPages" :source="page.src">
            </slot>
        </slider>
    </div>
    
    
</template>
<style scoped>
.item, .slider-item {
    font-size: 80px;
}
.slider {
    height: 700px;
}
</style>
<script>

export default {
    components: {
        'slider-page': require("./SliderPage")
    },

    props: {
        pages: {
            type: Array,
            default: []
        }
    },
    data() {
        return {
            items: [
                'a',
                'b'
            ],
            limitPages: [],
            index: 0,
            skipEvent: false,
            once: false,
            event: null,
            keepIndex: true
        }
    },
    created() {
        console.log(this.limitPages)
        
        this.limitPages = this.pages// .slice(0, 4)
        console.debug("created")
        // console.debug(this.pages[0].src)

        setInterval(() => {
            
            if (this.once) {
                console.debug(this.index)
                // this.update()
                setTimeout(() => {
                    this.update()
                }, 1000)
                this.once = false
            }
        }, 500)
    },

    methods: {
        onChange(event) {
        //     return 
        //     console.debug('change called')
            console.debug(`event index is ${event.index}, data index is ${this.index}`)
            this.index = event.index
            this.event = event
            this.once = true
        },

        update() {
            const event = this.event
            console.debug(`event index is ${event.index}, data index is ${this.index}`)

            let start = event.index - 1 < 0 ? 0 : event.index - 1;
            let end = event.index + 2

            if (start < 1) {
                this.once = false
                return
            }

            console.debug(`start ${start} end ${end}`)
            this.limitPages = this.pages.slice(start, end)
            this.index = this.event.index - 1
            console.debug(`first page index ${this.limitPages[0].index}`)

            for (var limitPage of this.limitPages) {
                console.debug(`src ${limitPage.src} index ${limitPage.index}`)
            }

            
        }
    }
}
</script>