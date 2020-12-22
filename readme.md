# esbuild svelte plugin example

This is an easy-to-run implementation of the esbuild svelte plugin sample code at https://esbuild.github.io/plugins/#svelte-plugin

## Install

1. Clone this repository
2. `npm install`

## Build

```
node .
```

## Run

Serve the `dist` directory in a local web server and navigate to it in your browser. There is no watcher, so you will have to re-run the build script manually if you change the example.

e.g., with [Site.js](https://sitejs.org), you’d do:

```
site dist
```

## But I want a watcher, damn it!

Calm down, this is just a simple example :)

See the [esbuild `serve` API](https://esbuild.github.io/api/#serve) for one way to implement a watcher.

In a nutshell, to use it, you would modify the `build` call to a `serve` call in `build.js`:

```js
require('esbuild').serve({}, {
```

And then include `app.js` in `dist/index.html` from the local server this creates:

```html
<script type="module" src="http://localhost:8000/app.js"></script>
```

And then, finally, after running `node .` to start the esbuild server, you would serve the `dist` folder separately with a web server like [Site.js](https://sitejs.org).

Note that even after all this you will still have to refresh your browser to see the changes. All this does is automate the build process when source code changes, it doesn’t implement Hot Module Replacement (HMR). If you want that, look at [esm-hmr](https://github.com/snowpackjs/esm-hmr).
