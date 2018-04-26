# wepy-preload-image -- 小程序图片加载组件

## 简介:

可用于图片的预加载， 类似于`web`上 `new` 一个 `Image` 对象进行加载；
主要用于加载线上的图片；

相比于`wx.previewImage`或者`wx.getImageInfo`, 其主要是用于 **确保图片已经加载进内存中**, 可用于控制 ：

1. `loading`的展示与隐藏；
2. 设置时可直接展示，不会看到图片片状加载；

## 更新：

## 使用姿势：

1. 引用:

`import MTPreload from 'wepy-preload-image'`;

2. 添加 `components`:

`components = { MTPreload }`; 

3. `template` 中使用:

```html
<!-- 初始化时加载图片 -->
<MTPreload :loadList="loadList"></MTPreload>
```

两种使用姿势:

1. 页面初始化时直接预加载:

```js
    // 通过 loadList 传入组件；
    data: {
        loadList: ['url1', 'urls'],
    }
```

2. js中使用:

```js
// url: 图片地址；
// String/Array
this.$invoke('./MTPreload', 'load', urlArray, data=>{
    console.log('加载成功', data);
    // data = {
    //     url : url，
    //     width: 图片宽度，
    //     height: 图片高度，
    // }
}, error => {
    console.log('加载失败');
});
```

