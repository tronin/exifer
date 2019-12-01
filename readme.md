<p align="center">
  <img src="exifer.png" alt="exifer" width="350" />
</p>

<p align="center">
  <a href="https://npmjs.org/package/exifer">
    <img src="https://badgen.now.sh/npm/v/exifer" alt="version" />
  </a>
  <a href="https://unpkg.com/exifer">
    <img src="http://img.badgesize.io/https://unpkg.com/exifer/dist/exifer.mjs?compression=gzip" alt="gzip size" />
  </a>
  <a href="https://github.com/terkelg/exifer/blob/master/LICENSE">
    <img src="https://img.shields.io/npm/l/exifer.svg" alt="license" />
  </a>
  <a href="https://github.com/terkelg/exifer/blob/master/package.json">
    <img src="https://img.shields.io/badge/dependencies-none-ff69b4.svg" alt="dependencies" />
  </a>
</p>

<p align="center"><b>A small 1.5kb exif meta-data reader</b></p>


Exifer do not analyze or parse the data. It's up to you as a consumer. I find it uncessecary in most use-cases. It's easier to build logic around numbers than magic strings.

Handy when you want to extract features from an image before upload, chekc rotation etc.

**~~lack of~~ Features**
- Small
- Vanilla JS
- Works on both server and client side
- Zero Dependencies


## Install

```
$ npm install exifer
```

This module exposes three module definitions:

* **ES Module**: `dist/exifer.mjs`
* **UMD**: `dist/exifer.umd.js`
* **CommonJS**: `dist/exifer.js`

Include skaler:
```js
// ES6
import exifer from 'exifer'

// CJS
const exifer = require('exifer');
```

The script can also be directly included from [unpkg.com](https://unpkg.com):
```html
<script src="https://unpkg.com/exifer"></script>
```


## Usage

```js
import exifer from 'exifer';

/**
 * Assume 'input' is the value coming from an input field:
 * <input type="file" accept="image/*" id="input" >
 */

const input = document.getElementById('#input').files[0];

const file = await exifer(input);
// ~> resized image as a File object - half the size

const file = await exifer(input);
// ~> resized image as a File object - 300px width

const file = await exifer(input);
// ~> resized image as a File object - stretched to 300x500px

```


## API

### exifer(input, options={})
Returns: `object` <_Promise_>

Reutnrs promise that resolves to the resized [`File`](https://developer.mozilla.org/en-US/docs/Web/API/File) object.

> **Note**:The new files has an updated ` last modified time` property.

#### input
Type: `File|Buffer|ArrayBuffer`

[`File`](https://developer.mozilla.org/en-US/docs/Web/API/File)

> **Note**: The file is expected to be of type image.

#### options.exif
Type: `object`<br>

IFD: Image Tags

Find the full list of avlaible tags [here](https://www.exiv2.org/tags.html)

> **Note**: The `width` and `height` options are ignored if `scale` is provided.

#### options.gps
Type: `object`<br>

IFD: GPSInfo Tags

Find the full list of avlaible tags [here](https://www.exiv2.org/tags.html)

```js
let file = await skaler(input, { width: 200 });
// ~> output is 200px width
```

## Credit

## License

MIT © [Terkel Gjervig](https://terkel.com)