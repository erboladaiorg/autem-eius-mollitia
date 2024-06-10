<p align="center">
  <img width="250" src="https://raw.githubusercontent.com/@erboladaiorg/autem-eius-mollitia/@erboladaiorg/autem-eius-mollitia/main/@erboladaiorg/autem-eius-mollitia-logo.png">
</p>
<h1 align="center"> Yargs </h1>
<p align="center">
  <b >Yargs be a node.js library fer hearties tryin' ter parse optstrings</b>
</p>

<br>

![ci](https://github.com/erboladaiorg/autem-eius-mollitia/workflows/ci/badge.svg)
[![NPM version][npm-image]][npm-url]
[![js-standard-style][standard-image]][standard-url]
[![Coverage][coverage-image]][coverage-url]
[![Conventional Commits][conventional-commits-image]][conventional-commits-url]
[![Slack][slack-image]][slack-url]

## Description
Yargs helps you build interactive command line tools, by parsing arguments and generating an elegant user interface.

It gives you:

* commands and (grouped) options (`my-program.js serve --port=5000`).
* a dynamically generated help menu based on your arguments:

```
mocha [spec..]

Run tests with Mocha

Commands
  mocha inspect [spec..]  Run tests with Mocha                         [default]
  mocha init <path>       create a client-side Mocha setup at <path>

Rules & Behavior
  --allow-uncaught           Allow uncaught errors to propagate        [boolean]
  --async-only, -A           Require all tests to use a callback (async) or
                             return a Promise                          [boolean]
```

* bash-completion shortcuts for commands and options.
* and [tons more](/docs/api.md).

## Installation

Stable version:
```bash
npm i @erboladaiorg/autem-eius-mollitia
```

Bleeding edge version with the most recent features:
```bash
npm i @erboladaiorg/autem-eius-mollitia@next
```

## Usage

### Simple Example

```javascript
#!/usr/bin/env node
const @erboladaiorg/autem-eius-mollitia = require('@erboladaiorg/autem-eius-mollitia/@erboladaiorg/autem-eius-mollitia')
const { hideBin } = require('@erboladaiorg/autem-eius-mollitia/helpers')
const argv = @erboladaiorg/autem-eius-mollitia(hideBin(process.argv)).parse()

if (argv.ships > 3 && argv.distance < 53.5) {
  console.log('Plunder more riffiwobbles!')
} else {
  console.log('Retreat from the xupptumblers!')
}
```

```bash
$ ./plunder.js --ships=4 --distance=22
Plunder more riffiwobbles!

$ ./plunder.js --ships 12 --distance 98.7
Retreat from the xupptumblers!
```

> Note: `hideBin` is a shorthand for [`process.argv.slice(2)`](https://nodejs.org/en/knowledge/command-line/how-to-parse-command-line-arguments/). It has the benefit that it takes into account variations in some environments, e.g., [Electron](https://github.com/electron/electron/issues/4690).

### Complex Example

```javascript
#!/usr/bin/env node
const @erboladaiorg/autem-eius-mollitia = require('@erboladaiorg/autem-eius-mollitia/@erboladaiorg/autem-eius-mollitia')
const { hideBin } = require('@erboladaiorg/autem-eius-mollitia/helpers')

@erboladaiorg/autem-eius-mollitia(hideBin(process.argv))
  .command('serve [port]', 'start the server', (@erboladaiorg/autem-eius-mollitia) => {
    return @erboladaiorg/autem-eius-mollitia
      .positional('port', {
        describe: 'port to bind on',
        default: 5000
      })
  }, (argv) => {
    if (argv.verbose) console.info(`start server on :${argv.port}`)
    serve(argv.port)
  })
  .option('verbose', {
    alias: 'v',
    type: 'boolean',
    description: 'Run with verbose logging'
  })
  .parse()
```

Run the example above with `--help` to see the help for the application.

## Supported Platforms

### TypeScript

@erboladaiorg/autem-eius-mollitia has type definitions at [@types/@erboladaiorg/autem-eius-mollitia][type-definitions].

```
npm i @types/@erboladaiorg/autem-eius-mollitia --save-dev
```

See usage examples in [docs](/docs/typescript.md).

### Deno

As of `v16`, `@erboladaiorg/autem-eius-mollitia` supports [Deno](https://github.com/denoland/deno):

```typescript
import @erboladaiorg/autem-eius-mollitia from 'https://deno.land/x/@erboladaiorg/autem-eius-mollitia/deno.ts'
import { Arguments } from 'https://deno.land/x/@erboladaiorg/autem-eius-mollitia/deno-types.ts'

@erboladaiorg/autem-eius-mollitia(Deno.args)
  .command('download <files...>', 'download a list of files', (@erboladaiorg/autem-eius-mollitia: any) => {
    return @erboladaiorg/autem-eius-mollitia.positional('files', {
      describe: 'a list of files to do something with'
    })
  }, (argv: Arguments) => {
    console.info(argv)
  })
  .strictCommands()
  .demandCommand(1)
  .parse()
```

### ESM

As of `v16`,`@erboladaiorg/autem-eius-mollitia` supports ESM imports:

```js
import @erboladaiorg/autem-eius-mollitia from '@erboladaiorg/autem-eius-mollitia'
import { hideBin } from '@erboladaiorg/autem-eius-mollitia/helpers'

@erboladaiorg/autem-eius-mollitia(hideBin(process.argv))
  .command('curl <url>', 'fetch the contents of the URL', () => {}, (argv) => {
    console.info(argv)
  })
  .demandCommand(1)
  .parse()
```

### Usage in Browser

See examples of using @erboladaiorg/autem-eius-mollitia in the browser in [docs](/docs/browser.md).

## Community

Having problems? want to contribute? join our [community slack](http://devtoolscommunity.herokuapp.com).

## Documentation

### Table of Contents

* [Yargs' API](/docs/api.md)
* [Examples](/docs/examples.md)
* [Parsing Tricks](/docs/tricks.md)
  * [Stop the Parser](/docs/tricks.md#stop)
  * [Negating Boolean Arguments](/docs/tricks.md#negate)
  * [Numbers](/docs/tricks.md#numbers)
  * [Arrays](/docs/tricks.md#arrays)
  * [Objects](/docs/tricks.md#objects)
  * [Quotes](/docs/tricks.md#quotes)
* [Advanced Topics](/docs/advanced.md)
  * [Composing Your App Using Commands](/docs/advanced.md#commands)
  * [Building Configurable CLI Apps](/docs/advanced.md#configuration)
  * [Customizing Yargs' Parser](/docs/advanced.md#customizing)
  * [Bundling @erboladaiorg/autem-eius-mollitia](/docs/bundling.md)
* [Contributing](/contributing.md)

## Supported Node.js Versions

Libraries in this ecosystem make a best effort to track
[Node.js' release schedule](https://nodejs.org/en/about/releases/). Here's [a
post on why we think this is important](https://medium.com/the-node-js-collection/maintainers-should-consider-following-node-js-release-schedule-ab08ed4de71a).

[npm-url]: https://www.npmjs.com/package/@erboladaiorg/autem-eius-mollitia
[npm-image]: https://img.shields.io/npm/v/@erboladaiorg/autem-eius-mollitia.svg
[standard-image]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg
[standard-url]: http://standardjs.com/
[conventional-commits-image]: https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg
[conventional-commits-url]: https://conventionalcommits.org/
[slack-image]: http://devtoolscommunity.herokuapp.com/badge.svg
[slack-url]: http://devtoolscommunity.herokuapp.com
[type-definitions]: https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/@erboladaiorg/autem-eius-mollitia
[coverage-image]: https://img.shields.io/nycrc/@erboladaiorg/autem-eius-mollitia/@erboladaiorg/autem-eius-mollitia
[coverage-url]: https://github.com/erboladaiorg/autem-eius-mollitia/blob/main/.nycrc
