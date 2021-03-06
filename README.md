# spore-wepy-tipbox

类toast提示窗口，但只显示文字，可调整显示位置。用于小程序wepy框架

## Demo

![demo](http://tabspace.github.io/demo/spore-wepy-tipbox/images/demo.gif)

## Getting Started

Install

```shell
npm i spore-wepy-tipbox
```

Example:

```html
<style lang="less"></style>
<template>
    <view class="container">
        <button @tap="showTip" size="mini" data-pos="center">显示到中间</button>
        <button @tap="showTip" size="mini" data-pos="top">显示到上方</button>
        <button @tap="showTip" size="mini" data-pos="bottom">显示到下方</button>
        <tip />
    </view>
</template>
<script>
import wepy from 'wepy';
import TipBox from 'spore-wepy-tipbox';

export default class Index extends wepy.page {
    config = {
        navigationBarTitleText: '首页'
    };
    components = {
        tip: TipBox
    };
    methods = {
        showTip(evt) {
            let pos = evt.currentTarget.dataset.pos;
            this.$invoke('tip', 'show', 'position:' + pos, {
                position: pos
            });
        }
    };
}
</script>
```

## Parameters

### text

Type: `String`

要显示的文案

### options

Type: `Object`

tipbox 浮层选项

#### options.position

Type: `String`

tipbox 浮层显示位置，可选值: ['top', 'bottom', 'center']

#### options.margin

Type: `String`

浮层与边界的距离，仅在 position 设置为 `'top'` 或者 `'bottom'` 时有效

Default: `'20px'`

#### options.duration

Type: `Number`

浮层动画显示时长，单位为 ms

Default: `2000`

## Release History

* 2018-06-20 v0.1.3 完善选项说明，提供 duration 选项
* 2018-02-11 v0.1.2 居中样式变更为使用 flex 方案，解决 transform 动画引发的位置偏移问题
* 2017-12-13 v0.1.1 修正部分机型浮层位置偏移问题
* 2017-08-08 v0.1.0 发布第一个正式版
