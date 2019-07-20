# Lazy Loader for html elements

lazyimg 是一个基于jQuery的懒加载图片组件。

ps:目前支持 `全局方法调用` 和 `jquery插件调用` 两种模式

## Getting started

首先确保先引入jquery，之后再引入lazyimg.js，它会产生一个名为`lazyimg`的全局对象，请避免重名。

生成环境地址：


### 同时支持 AMD, CommonJS, ES6 调用方式


CommonJS
``` javascript
var lazyimg = require('lazyimg');

//
lazyimg.config({

})

//
lazyimg.listen();

//
lazyimg.detch();

```

AMD 方式
``` javascript
require(['lazyimg'], function(lazyimg) {
　//
 lazyimg.config({

 })

 //
 lazyimg.listen();

 //
 lazyimg.detch();
});

```


ES6

``` javascript
import $ from 'jQuery';
import lazyimg from 'jquery-lazyimg';

$('img').lazyimg();
// 或者
lazyimg.listen();

```



### 加载前景图
```html
<img lazy-src="temp/1.jpg" alt="" />
```
lazyimg，所以如果只需要懒加载图片，可以不用传入参数
```js
lazyimg.listen();
```
相当于
```js
lazyimg.listen('img[lazy-src]', 'img');
```
如果需要在图片触发加载条件后执行回调，可将回调函数作为第三个参数传入
```js
lazyimg.listen('img[lazy-src]', 'img', function(obj) {
	// obj 是当前触发加载条件的jQuery对象
});
```

### 加载前景图 (jQuery 插件版本)
```html
<img lazy-src="temp/1.jpg" alt="" />
```
lazyimg，所以如果只需要懒加载图片，可以不用传入参数
```js
$('img').listen();
```

如果需要在图片触发加载条件后执行回调，可将回调函数作为第三个参数传入
```js
$('img').listen(function(obj) {
	// obj 是当前触发加载条件的jQuery对象
});
```


### 加载背景图
```html
<div class="bg" lazy-bg="temp/bg.jpg"></div>
```

```js
lazyimg.listen('.bg', 'bg', function(obj) {
	// 回调是可选的
});
```

### 加载背景图 (jQuery 插件版本)
```html
<div class="bg" lazy-bg="temp/bg.jpg"></div>
```

```js
$('.bg').listen('bg', function(obj) {
	// 回调是可选的
});
```

### Loading样式
lazyimg会给每个被监听的img元素加上一个class：`lazy-loading`，可以在项目的css中设置loading效果。


## Configuration
目前提供5个配置项，通过`config`方法设置,要在listen方法前调用。
```js
lazyimg.config({
    timeout: 10, // 每次滚动事件执行延迟
    buffer: 100, // 屏幕上下方缓冲区域高度
    loadingClass: 'lazy-loading',
    srcValue: 'lazy-src',
    bgValue: 'lazy-bg'
});
```


## Configuration(jQuery 插件版本)
目前提供5个配置项，只需要在第一个参数，配置就可以了。
```js
$('img').lazyimg({
    timeout: 10, // 每次滚动事件执行延迟
    buffer: 100, // 屏幕上下方缓冲区域高度
    loadingClass: 'lazy-loading',
    srcValue: 'lazy-src',
    bgValue: 'lazy-bg'
},'img',function(obj){

});
```



## Method

### detect

某些需要在特定事件中加载的内容，可以在各自的事件处理逻辑后调用此方法，以展示原本被隐藏的内容。
```js
lazyimg.detect();
```


### clear

清除对某个或全部对象的监听
```js
lazyimg.clear([DOM Object]);
```




## Method(jQuery 插件版本)

### detect

某些需要在特定事件中加载的内容，可以在各自的事件处理逻辑后调用此方法，以展示原本被隐藏的内容。
```js
$('img').lazyimg('detect');
```


### clear

清除对某个或全部对象的监听
```js
$('img').clear([DOM Object]);
```



