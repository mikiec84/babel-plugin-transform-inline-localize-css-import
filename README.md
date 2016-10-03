<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [babel-plugin-transform-inline-localize-css-import](#babel-plugin-transform-inline-localize-css-import)
  - [Quickstart](#quickstart)
  - [Configuration](#configuration)
  - [Test](#test)
  - [Release](#release)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# babel-plugin-transform-inline-localize-css-import

[![Version][version-svg]][package-url] [![Build Status][travis-svg]][travis-url] [![License][license-image]][license-url] [![Downloads][downloads-image]][downloads-url]

**Inline and localize `import`ed CSS files to {classNames, code}.**

This is similar to [css modules](https://github.com/css-modules/css-modules) localize as it will allow you to localize class names and animations.

## Quickstart

```sh
npm install babel-plugin-transform-inline-localize-css --save-dev
```

**.babelrc**
```json
{
  "plugins": [
    ["babel-plugin-transform-inline-localize-css", {
      "localFormat": "$cssFilename__$token"
    }]
  ]
}
```

**Component.css**
```css
.item {
  color: blue;
}

.itemSelected {
  color: yellow;
  animation-name: hide;
}

@keyframes hide {0%{opacity:0}}
```

**Component.js**
```js
import theme from './Component.css';
```

```sh
babel Component.js

# var theme = {
#   classNames: {
#     item: 'Component__item',
#     itemSelected: 'Component__itemSelected'
#   },
#   code: 'Component__item \n{  color: blue}\n\nComponent__itemSelected \n{  color: yellow;\nanimation-name: Component__hide }\n\n@keyframes Component__hide {0%{opacity: 0}}'
# }
```

## Configuration

* **localFormat** (`string`): How to localize tokens. Available variables:
  - `$cssFilename`: Filename, without extension, of the imported CSS file.
  - `$jsFilename`: Filename, without extension of the module JavaScript file.
  - `$token`: Current class name or animation-name to replace.

## Test

```sh
npm test
```

## Release

```sh
npm run release
```

[version-svg]: https://img.shields.io/npm/v/babel-plugin-transform-inline-localize-css.svg?style=flat-square
[package-url]: https://npmjs.org/package/babel-plugin-transform-inline-localize-css
[travis-svg]: https://img.shields.io/travis/algolia/babel-plugin-transform-inline-localize-css/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/algolia/babel-plugin-transform-inline-localize-css
[license-image]: http://img.shields.io/badge/license-MIT-green.svg?style=flat-square
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/babel-plugin-transform-inline-localize-css.svg?style=flat-square
[downloads-url]: http://npm-stat.com/charts.html?package=babel-plugin-transform-inline-localize-css
