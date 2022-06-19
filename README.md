# Image Gen
This is an api wrapper built for apis compatible with [DankMemer's imagen](https://github.com/DankMemer/imgen). They privatized their public instance, so I've made my own along with this wrapper that uses [my instance](https://imgen.yiff.rest/) by default, but is compatible with any instances that function the same.

[![](https://nodei.co/npm/imgen.png)](https://npm.im/imgen)

## JavaScript Example:
```js
const ImageGenAPI = require("imgen");
const { writeFile } = require("fs/promises");
// only apiKey is required
const gen = new ImageGenAPI({ apiKey: "api key", userAgent: "SomeUserAgent/1.0.0", baseURL: "https://imgen.yiff.rest/api" });
gen.abandon("text to provide").then(response => writeFile(`${__dirname}/abandon.png`, response.file));
```

## TypeScript Example:
```ts
import ImageGenAPI from "imgen";
import { writeFile } from "fs/promises";
// only apiKey is required
const gen = new ImageGenAPI({ apiKey: "api key", userAgent: "SomeUserAgent/1.0.0", baseURL: "https://imgen.yiff.rest/api" });
gen.abandon("text to provide").then(response => writeFile(`${__dirname}/abandon.png`, response.file));
```

The return of the functions is this structure (using the TS interface as an example):
```ts
interface RequestResponse {
    ext: string;
    mime: string;
    file: Buffer;
}
```
`ext` will be the file extension of what was returned, `mime` will be the mime type of what was returned, and `file` will be the actual data returned.

The only function that differentiates from this is the `yomomma` function, which returns just a string.
