Slider infinite
================

拷贝`example/src/components/`目录内的`SliderInfinite`和`SliderPage`到自己的组件目录。

# Guide

```
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
```

slider-page 有一个必要参数。pages，需要绑定的数据，且必须是一个对象数组。


slider-infinite的子组件必须是slider-page，且必须包含三个属性。

page是pages内的每一项数据。

index是slider-page的索引编号。slider-index是slider-infinite的当前索引。SliderPage中根据这两个数据计算是否需要渲染，达到懒加载的目的。