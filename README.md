
[简体中文](README.zh_CN.md) | [English](README.md)

# About 

Photomaker is an image compression component that supports multiple processing methods, including Vuepress and command line. It supports various image formats such as JPG, GIF, and PNG.

Currently, it only supports Vuepress v2.x and command line.

<br>

# Vuepress Usage

## install
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


## how to use

```js
// vuepress v2.x
// docs/.vuepress/client.ts
import { vuepressPhotomaker } from "photomaker";
export default defineUserConfig({
  plugins: [
    vuepressPhotomaker({
        // you can set options here
    })
  ],
});
```



more


```js
// vuepress v2.x
// docs/.vuepress/client.ts
import { vuepressPhotomaker } from "photomaker";
export default defineUserConfig({
  plugins: [
    vuepressPhotomaker({
        ext: 'jpg,png,gif',  // deal with jpg,png,gif
        webp: true,   // convert to webp
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

## Notice

for Vuepress

- Photomaker only processes local images and does not support remote images.

- It only processes all relevant images under the app.dir.public() path, such as docs/.vuepress/public.

- Photomaker does not modify the original images. Instead, it creates a new folder called photomaker under the app.dir.public() directory to store and reference the new files.

<br>

# Command line Usage


## install
<br>

```bash
npm install photomaker -g
```


## how to use

```bash
photomaker -i ./input -o ./output
```


## Command Line Argument Description


`i` The path to be processed, required

`o` The output path, optional, default is photomaker

`e` The file format to be processed, optional, default is jpg, gin, jpeg, png

`p` Whether to convert to webp, optional, default is false

`q` The image compression quality, optional, default is 80

`w` The image scaling height, optional

`h` The image scaling width, optional

`f` The image scaling adaptation method, optional

`b` The image scaling background fill color, optional, default is black

For detailed parameter descriptions, please see the common parameter description below.

<br>





## Config file

By default, photomaker will read the pmConfig.json file, which takes the highest priority. If this file exists, the command-line arguments will be ignored.

To create the `pmConfig.json` file, go to the current directory where photomaker will be executed, for example, /Users/xxx/project/ in macOS.

The content of the pmConfig.json file should be as follows:

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

# Common Argument Description

`input` A required string parameter that specifies the path to be processed. Note: Only supports command-line configuration file.

`output` An optional string parameter that specifies the output path. Default value is photomaker. Note: Only supports command-line configuration file.

`ext` An optional string parameter that specifies the image file format to be processed. Default value is jpg,jpeg,gif,png. For example, jpg means only jpg files will be processed.

`quality` An optional integer parameter that specifies the image compression quality. Default value is 80.

`webp` An optional boolean parameter that specifies whether to convert all png/gif/jpg formats to webp format. Default value is false.

`resize` An optional object parameter that specifies the image scaling process.

`resize.width` An optional integer parameter that specifies the width of the image after scaling.

`resize.height` An optional integer parameter that specifies the height of the image after scaling.

`resize.fit` An optional string parameter that specifies the scaling adaptation method. Default value is cover, other options include contain, fill, inside, outside.


If both width and height are provided, the following methods can be used to fit the image to these dimensions:

- cover: (default) Maintain aspect ratio and crop/clips the image to cover the provided width and height.

- contain: Maintain aspect ratio and use "letterboxing" if necessary to contain the image within the provided width and height.

- fill: Ignore the aspect ratio of the input image and stretch it to the provided width and height.

- inside: Maintain aspect ratio and resize the image to be as large as possible while ensuring its dimensions are less than or equal to the specified width and height.

- outside: Maintain aspect ratio and resize the image to be as small as possible while ensuring its dimensions are greater than or equal to the specified width and height.

`resize.background` An optional string parameter that specifies the background color to be used when the fit option is set to contain and there is extra space. Default value is black (#000000). 

Only hexadecimal colors are supported:

- Three-digit hexadecimal color, e.g. #000.
- Six-digit hexadecimal color, e.g. #000000.
- Eight-digit hexadecimal color with alpha channel, e.g. #ffffff00 for transparent background.

<br>

# Buy me a cup of coffee

The creative process is both challenging and time-consuming. If you could buy me a cup of coffee and give me some encouragement, it would help me continue to work hard and produce more valuable content. Thank you very much.

Please click the link below to support me, thanks

[Paypal](https://paypal.me/ssttm169)

