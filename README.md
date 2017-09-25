# Webpack Guide

Notes from the [Webpack Guides](https://webpack.js.org/guides/getting-started/)

## [Getting Started](https://webpack.js.org/guides/getting-started/)

Start a new npm project with `npm init -y`

There are problems with managing JavaScript projects without Webpack:

- It is not immediately apparent which scripts depends on an external libraries.
- If dependencies are missing, or included in the wrong order, the application will not function properly.
- If a dependency is included but not used, the browser will be forced to download unnecessary code.

### ES6 modules

The import and export statements have been standardized in ES2015. Although they are not supported in most browsers yet, webpack does support them out of the box.

### Config file

Webpack uses `webpack.config.js`. If a `webpack.config.js` is present, the webpack command picks it up by default.

#### --config flag

Use the `--config` option to pass a config of any name. This will come in useful for more complex configurations that need to be split into multiple files.

## [Asset Management](https://webpack.js.org/guides/asset-management/)

### Introduce modules and loaders

```
module: {
  rules: [{
    test: /\.css$/,
    use: [
      'style-loader',
      'css-loader'
    ]
  }]
```

Loaders are how content is modified. `test` searches for extensions. `use` is a collection of loaders
