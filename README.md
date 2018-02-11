# spore-wepy-tipbox
类toast提示窗口，但只显示文字，可调整显示位置。用于小程序wepy框架

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
		<button @tap="showTip" size="mini" data-pos="center">普通tip</button>
		<button @tap="showTip" size="mini" data-pos="top">上方tip</button>
		<button @tap="showTip" size="mini" data-pos="bottom">下方tip</button>
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

tipbox 浮层显示位置，可选值: ['top', 'bottom']

#### options.margin

Type: `String`

Default: `'20px'`

tipbox 浮层边距

## Release History

 * 2018-02-11 v0.1.2 居中样式变更为使用flex布局，解决transform动画引发的位置偏移问题
 * 2017-12-13 v0.1.1 修正部分机型弹框位置偏移问题
 * 2017-08-08 v0.1.0 发布第一个正式版
