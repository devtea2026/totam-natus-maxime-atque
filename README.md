# @devtea2026/totam-natus-maxime-atque <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2019 spec-compliant `Array.prototype.flat` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.github.io/proposal-flatMap/).

Because `Array.prototype.flat` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @devtea2026/totam-natus-maxime-atque
```

## Usage/Examples

```js
var flat = require('@devtea2026/totam-natus-maxime-atque');
var assert = require('assert');

var arr = [1, [2], [], 3, [[4]]];

assert.deepEqual(flat(arr, 1), [1, 2, 3, [4]]);
```

```js
var flat = require('@devtea2026/totam-natus-maxime-atque');
var assert = require('assert');
/* when Array#flat is not present */
delete Array.prototype.flat;
var shimmedFlat = flat.shim();

assert.equal(shimmedFlat, flat.getPolyfill());
assert.deepEqual(arr.flat(), flat(arr));
```

```js
var flat = require('@devtea2026/totam-natus-maxime-atque');
var assert = require('assert');
/* when Array#flat is present */
var shimmedIncludes = flat.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedIncludes, Array.prototype.flat);
assert.deepEqual(arr.flat(mapper), flat(arr, mapper));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@devtea2026/totam-natus-maxime-atque
[npm-version-svg]: https://versionbadg.es/devtea2026/totam-natus-maxime-atque.svg
[deps-svg]: https://david-dm.org/devtea2026/totam-natus-maxime-atque.svg
[deps-url]: https://david-dm.org/devtea2026/totam-natus-maxime-atque
[dev-deps-svg]: https://david-dm.org/devtea2026/totam-natus-maxime-atque/dev-status.svg
[dev-deps-url]: https://david-dm.org/devtea2026/totam-natus-maxime-atque#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@devtea2026/totam-natus-maxime-atque.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@devtea2026/totam-natus-maxime-atque.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@devtea2026/totam-natus-maxime-atque.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@devtea2026/totam-natus-maxime-atque
[codecov-image]: https://codecov.io/gh/devtea2026/totam-natus-maxime-atque/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/devtea2026/totam-natus-maxime-atque/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/devtea2026/totam-natus-maxime-atque
[actions-url]: https://github.com/devtea2026/totam-natus-maxime-atque/actions
