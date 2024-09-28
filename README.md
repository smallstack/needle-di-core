# Needle DI 💉

> A lightweight, type-safe Dependency Injection (DI) library for JavaScript and TypeScript projects.

[![NPM version](http://img.shields.io/npm/v/needle-di.svg?style=flat-square)](https://www.npmjs.com/package/needle-di)
[![NPM downloads](http://img.shields.io/npm/dm/needle-di.svg?style=flat-square)](https://www.npmjs.com/package/needle-di)
[![Build status](https://github.com/dirkluijk/needle-di/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/dirkluijk/needle-di/actions/workflows/main.yml)

Needle DI is a lightweight, TypeScript-first library for dependency injection (DI). It is designed to be both easy to use and highly efficient.

### Key Features

- Stand-alone: No additional dependencies required
- Intended for both JavaScript-only and TypeScript projects
- Supports [tree-shakeable injection tokens](https://needle-di.io/advanced/tree-shaking.html): optimize your builds for production.
- Inspired by [Angular](https://angular.dev/) and [InversifyJS](https://github.com/inversify/InversifyJS), familiar to developers coming from these frameworks.
- Uses native [ECMAScript TC39 decorators](https://github.com/tc39/proposal-decorators) (currently stage 3)
- No need for `experimentalDecorators` and `emitDecoratorMetadata`
- No reflection libraries needed, like `reflect-metadata` or other reflection mechanisms.

## Basic example

Here’s a simple example using constructor injection to inject one service into another.

```typescript
import { injectable, inject } from "needle-di";

@injectable()
class FooService {}

@injectable()
class BarService {
  constructor(private fooService = inject(FooService)) {}
  //                  ^? Type will be inferred as `FooService`
}
```

The `@injectable` decorator eliminates the need to manually register services. To construct the `BarService`, create a
dependency injection container, and use the `container.get()` method:

```typescript
import { Container } from "needle-di";

const container = new Container();
const barService = container.get(BarService);
//    ^? Type will be inferred as `BarService`
```

Check out the [docs](https://needle-di.io/concepts/binding.html) to learn more!

## Installation

```
npm install --save needle-di
```

## Docs

Check out our docs on [https://needle-di.io](https://needle-di.io/concepts/binding.html).

## License

License under the MIT License (MIT)

Copyright (c) 2024 Dirk Luijk

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

