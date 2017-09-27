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

Prior to webpack, front-end developers would use tools like grunt and gulp to process these assets and move them from their /src folder into their /dist or /build directory. The same idea was used for JavaScript modules, but tools like webpack will dynamically bundle all dependencies (creating what's known as a dependency graph). This is great because every module now explicitly states its dependencies and we'll avoid bundling modules that aren't in use.

One of the coolest webpack features is that you can also include any other type of file, besides JavaScript, for which there is a loader. This means that the same benefits listed above for JavaScript (e.g. explicit dependencies) can be applied to everything used in building a website or web app.

### Loaders

Webpack connect specific file extensions to processing rules, called "loaders." The naming convention is to call your tool `*-loader`.

Webpack uses a regular expression to determine which files it should look for and serve to a specific loader. In this case any file that ends with .css will be served to the `style-loader` and the `css-loader`.

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

#### Style Loader

This enables you to import './style.css' into the file that depends on that styling. Now, when that module is run, a <style> tag with the stringified css will be inserted into the <head> of your html file.

#### CSS-loader

The `css-loader` interprets `@import` and `url()` like `import/require()` and will resolve them.

### It's all about Loaders

Before we continue, recognize that all future assets, like images, icons, and fonts will follow the same pattern. We will add a rule that will do the same thing;

1. define the extension to _test_ using `test:`

2. define which loaders to use using `use:`

The real trick is to have a problem to solve and stop and think about what loader you can use that already exists because, it certainly exists.

#### Loading Images and Fonts

The `file-loader` is a multi-purpose loader that instructs webpack to emit the required object as file and to return its public url.

## Entry & Output

`entry` is the property which manages the files created for consumption by linking the key, or file name with the source location to be ingested.

`output` has a `filename` property which will resolve each key in `entry` and populate the `[name]` variable with each `entry` key. In this example, output will put a `app.bundle.js` and `print.bundle.js` into the `/dist` directory as stated in `path`

```
entry: {
  app: './src/index.js',
  print: './src/print.js'
},
output: {
  filename: '[name].bundle.js',
  path: path.resolve(__dirname, 'dist')
}
```
