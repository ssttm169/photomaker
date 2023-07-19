
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

Please click button below to support me, thanks

<a href=" https://paypal.me/ssttm169" target="_blank">
 <svg xmlns="http://www.w3.org/2000/svg"  width="150" height="60" viewBox="0 0 338.667 89.785"><g transform="translate(936.898 -21.779)"><path clip-path="none" d="M-828.604 39.734c-.697 0-1.289.506-1.398 1.195l-8.068 51.165a1.31 1.31 0 0 0 1.294 1.513h9.568c.696 0 1.289-.507 1.398-1.195l2.37-15.025c.108-.688.701-1.195 1.398-1.195h8.699c10.164 0 18.792-7.416 20.368-17.465 1.589-10.134-6.328-18.971-17.549-18.993zm9.301 11.422h6.96c5.73 0 7.596 3.381 7.006 7.12-.59 3.747-3.488 6.507-9.031 6.507h-7.084zm45.788 3.478c-2.416.009-5.196.504-8.317 1.804-7.159 2.984-10.597 9.151-12.057 13.647 0 0-4.647 13.717 5.852 21.253 0 0 9.737 7.255 20.698-.447l-.189 1.203a1.31 1.31 0 0 0 1.292 1.513h9.083c.697 0 1.289-.507 1.398-1.195l5.525-35.038a1.31 1.31 0 0 0-1.292-1.515h-9.083c-.697 0-1.29.507-1.398 1.195l-.297 1.886s-3.967-4.333-11.216-4.306zm.297 11.067c1.043 0 1.997.144 2.853.419 3.919 1.258 6.141 5.023 5.498 9.104-.793 5.025-4.914 8.725-10.199 8.725-1.042 0-1.996-.143-2.853-.418-3.918-1.258-6.154-5.023-5.511-9.104.793-5.025 4.927-8.727 10.212-8.727z" fill="#003087"/><path clip-path="none" d="M-697.804 39.734c-.697 0-1.289.506-1.398 1.195l-8.068 51.165a1.31 1.31 0 0 0 1.294 1.513h9.568c.696 0 1.289-.507 1.398-1.195l2.37-15.025c.108-.688.701-1.195 1.398-1.195h8.699c10.164 0 18.791-7.416 20.366-17.465 1.59-10.134-6.326-18.971-17.547-18.993zm9.301 11.422h6.96c5.73 0 7.596 3.381 7.006 7.12-.59 3.747-3.487 6.507-9.031 6.507h-7.084zm45.787 3.478c-2.416.009-5.196.504-8.317 1.804-7.159 2.984-10.597 9.151-12.057 13.647 0 0-4.645 13.717 5.854 21.253 0 0 9.735 7.255 20.697-.447l-.189 1.203a1.31 1.31 0 0 0 1.294 1.513h9.082c.697 0 1.289-.507 1.398-1.195l5.527-35.038a1.31 1.31 0 0 0-1.294-1.515h-9.083c-.697 0-1.29.507-1.398 1.195l-.297 1.886s-3.967-4.333-11.216-4.306zm.297 11.067c1.043 0 1.997.144 2.853.419 3.919 1.258 6.141 5.023 5.498 9.104-.793 5.025-4.914 8.725-10.199 8.725-1.042 0-1.996-.143-2.853-.418-3.918-1.258-6.154-5.023-5.511-9.104.793-5.025 4.927-8.727 10.212-8.727z" fill="#0070e0"/><path clip-path="none" d="M-745.92 55.859c-.72 0-1.232.703-1.012 1.388l9.958 30.901-9.004 14.562c-.437.707.071 1.62.902 1.62h10.642a1.77 1.77 0 0 0 1.513-.854l27.811-46.007c.427-.707-.083-1.611-.909-1.611h-10.641a1.77 1.77 0 0 0-1.522.869l-10.947 18.482-5.557-18.345c-.181-.597-.732-1.006-1.355-1.006z" fill="#003087"/><path clip-path="none" d="M-609.107 39.734c-.696 0-1.289.507-1.398 1.195l-8.07 51.163a1.31 1.31 0 0 0 1.294 1.515h9.568c.696 0 1.289-.507 1.398-1.195l8.068-51.165a1.31 1.31 0 0 0-1.292-1.513z" fill="#0070e0"/><path clip-path="none" d="M-908.37 39.734a2.59 2.59 0 0 0-2.556 2.185l-4.247 26.936c.198-1.258 1.282-2.185 2.556-2.185h12.445c12.525 0 23.153-9.137 25.095-21.519a20.76 20.76 0 0 0 .245-2.793c-3.183-1.669-6.922-2.624-11.019-2.624z" fill="#001c64"/><path clip-path="none" d="M-874.832 42.359a20.76 20.76 0 0 1-.245 2.793c-1.942 12.382-12.571 21.519-25.095 21.519h-12.445c-1.273 0-2.358.926-2.556 2.185l-3.905 24.752-2.446 15.528a2.1 2.1 0 0 0 2.075 2.43h13.508a2.59 2.59 0 0 0 2.556-2.185l3.558-22.567a2.59 2.59 0 0 1 2.558-2.185h7.953c12.525 0 23.153-9.137 25.095-21.519 1.379-8.788-3.047-16.784-10.611-20.75z" fill="#0070e0"/><path clip-path="none" d="M-923.716 21.779c-1.273 0-2.358.926-2.556 2.183l-10.6 67.216c-.201 1.276.785 2.43 2.077 2.43h15.719l3.903-24.752 4.247-26.936a2.59 2.59 0 0 1 2.556-2.185h22.519c4.098 0 7.836.956 11.019 2.624.218-11.273-9.084-20.58-21.873-20.58z" fill="#003087"/></g></svg></a>