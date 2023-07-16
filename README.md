
# 简介

Photomaker 是一个图片压缩组件, 支持Vuepress, 命令行等多种处理方式。支持jpg, gif, png等多种图片格式。

目前只支持  vuepress v2.x版本 和 命令行

<br>

# Vuepress 使用方法

## 安装
<br>

npm
```bash
npm install photomaker --save-dev
```

yarn
```bash
yar add photomaker -D
```


pnpm
```bash
pnpm add -D photomaker
```


## 使用

```js
// vuepress v2.x
// docs/.vuepress/client.ts
import { vuepressPhotomaker } from "photomaker";
export default defineUserConfig({
  plugins: [
    vuepressPhotomaker({
        // 这里可以设置参数
    })
  ],
});
```



更多例子


```js
// vuepress v2.x
// docs/.vuepress/client.ts
import { vuepressPhotomaker } from "photomaker";
export default defineUserConfig({
  plugins: [
    vuepressPhotomaker({
        ext: 'jpg,png,gif',  // 处理jpg,png,gif为后缀的图片文件
        webp: true,   // 转成 webp文件格式
        quality: 80,
        resize: {
          width: 500,  
          height: 500,
          fit: "contain",
          background: "#ffffff00",
        },
    })
  ],
});
```

<br>

## 需要注要

photomaker 只处理本地图片, 不支持远程图片.

只对 app.dir.public() 路径下所有相关的图片进行处理, 例如是: docs/.vuepress/public 这个路径。

photomaker 不会改变原有图片, 在app.dir.public() 目录下新建一个 `photomaker` 文件夹, 存储和引用这些新的文件.

<br>

# 命令行使用方法


## 安装
<br>

```bash
npm install photomaker -g
```


## 使用

```bash
photomaker -i ./input -o ./output
```


## 命令行参数说明


`i` 需要处理的路径, 必填

`o` 需要输出的路径, 选填, 默认 photomaker

`e` 需要处理的文件格式, 选填, 默认 jpg,gin,jpeg,png

`p` 是否需要转成 webp, 选填, 默认 false

`q` 图片压缩质量, 选填, 默认 80

`w` 图片缩放高度, 选填

`h` 图片缩放宽度, 选填

`f` 图片缩放适配方式, 选填

`b` 图片缩放背景填充颜色, 选填, 默认黑色

详细参数说明请查看下面的通用参数说明

<br>





## 配置文件

默认会读取 pmConfig.json 文件,  这个优先级别最高, 存在文件, 会无视命令行的参数。

在执行的当前目录,  macos为例 `/Users/xxx/project/` 目录下, 新建 pmConfig.json

具体内容是如下：

```json
{
    "input": "./input",
    "output": "./output",
    "webp": true,
    "quality": 80,
    "resize": {
        "width": 500,
        "height": 500,
        "fit": "contain",
        "background": "#ffffff00"
    }
}
```

<br>

# 通用参数说明

`input` String类型, 必填, 需要处理的路径. 注: 只支持命令行配置文件方式

`output` String类型, 选填, 需要输出的路径, 默认是 photomaker, 注: 只支持命令行配置文件方式

`ext` String类型, 选填, 这个参数需要图片格式文件, 默认是 jpg,jpeg,gif,png, 例: jpg 这表示只处理jpg文件

`quality` Int类型, 选填, 图片压缩质量, 默认 80

`webp` Boolean类型, 选填, 这个参数表示是否把原有的png/gif/jpg格式, 统一转成webp格式, 默认是 false

`resize` 对象类型, 选填, 对图片进行缩放处理.

`resize.width` Int类型, 选填, 对图片进行宽度缩放处理.

`resize.height` Int类型, 选填, 对图片进行高度缩放处理.

`resize.fit` String类型, 选填, 对图片进行缩放处理适配方式, 默认cover, 其他包括 contain, fill, inside, outside

如果同时提供了 width 和 height , 则图像应适合这些宽度和高度的可能方法如下:

- cover:（默认）保持长宽比，通过裁剪/剪切确保图片覆盖提供的width 和 height。
- contain: 保持宽高比，必要时使用 "信箱 "将图像包含在提供的width 和 height内。
- fill:  忽略输入图像的宽高比，并拉伸至所提供的width 和 height。
- inside:  保持宽高比，调整图像大小至尽可能大，同时确保其尺寸小于或等于指定的width 和 height。
- outside: 在保证长宽比的情况下，将图像的尺寸调整为尽可能小，同时确保其尺寸大于或等于指定的width 和 height。

`resize.background` String类型, 选填, 当适配方式 fit 是 contain时, 多出的区域由指定这个背景色来填充, 默认是黑色(#000000)

只支持十六进制的颜色
- 支持的3位的十六进制的颜色, 例 #000
- 支持的6位的十六进制的颜色, 例 #000000
- 支持的8位的十六进制的颜色, 例 #ffffff00 这个透明背景

<br>

# 给我买杯咖啡

创作的路上, 即艰苦, 又耗时。给我买杯咖啡, 给我打打气, 助我继续努力输出更多更有价格的内容, 非常感谢。


<div  style="display:flex;justify-content: space-around;align-items: center;">
<div style="flex: 1; margin-right: 10px;">

微信支付

![wechat](https://www.itomtan.com/posts/other/wechat-pay.jpeg)
</div>

<div  style="flex: 1;margin-left: 10px;">

支付宝支付
![apipay](https://www.itomtan.com/posts/other/alipay.png)

</div>

</div>
