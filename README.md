# esbuild-plugin-dynamic-import

Deprecated: This plugin is unnecessary now because it has been supported by esbuild natively from [`v0.19.0`](https://github.com/evanw/esbuild/releases/tag/v0.19.0).

---

[![GitHub Actions](https://github.com/esbuildr/esbuild-plugin-dynamic-import/workflows/CI/badge.svg)](https://github.com/esbuildr/esbuild-plugin-dynamic-import/actions/workflows/ci.yml)
[![type-coverage](https://img.shields.io/badge/dynamic/json.svg?label=type-coverage&prefix=%E2%89%A5&suffix=%&query=$.typeCoverage.atLeast&uri=https%3A%2F%2Fraw.githubusercontent.com%2Fesbuildr%2Fesbuild-plugin-dynamic-import%2Fmain%2Fpackage.json)](https://github.com/plantain-00/type-coverage)
[![npm](https://img.shields.io/npm/v/esbuild-plugin-dynamic-import.svg)](https://www.npmjs.com/package/esbuild-plugin-dynamic-import)
[![GitHub Release](https://img.shields.io/github/release/esbuildr/esbuild-plugin-dynamic-import)](https://github.com/esbuildr/esbuild-plugin-dynamic-import/releases)

[![Conventional Commits](https://img.shields.io/badge/conventional%20commits-1.0.0-yellow.svg)](https://conventionalcommits.org)
[![Renovate enabled](https://img.shields.io/badge/renovate-enabled-brightgreen.svg)](https://renovatebot.com)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)
[![Code Style: Prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
[![changesets](https://img.shields.io/badge/maintained%20with-changesets-176de3.svg)](https://github.com/changesets/changesets)

Dynamic import variables support for esbuild

## TOC <!-- omit in toc -->

- [Usage](#usage)
  - [Install](#install)
  - [API](#api)
  - [Usage](#usage-1)
- [Sponsors](#sponsors)
- [Backers](#backers)
- [Changelog](#changelog)
- [License](#license)

## Usage

### Install

```sh
# pnpm
pnpm add -D esbuild-plugin-dynamic-import

# yarn
yarn add -D esbuild-plugin-dynamic-import

# npm
npm i -D esbuild-plugin-dynamic-import
```

### API

```js
import { dynamicImport } from 'esbuild-plugin-dynamic-import'

esbuild.build({
  plugins: [
    dynamicImport({
      // filter: // optional, default: /\.([cm]?[jt]s|[jt]sx)$/
      // ignore: // optional, default: /\bnode_modules\b/
      // loader: // optional, default: adjust with path extension
    }),
  ],
})
```

### Usage

```js
const lazyImport = () => import(`./pages/${page}`)

// comments are allowed
const lazyImport = () =>
  import(
    /* comment1 */ // inline comment
    /**
     * multiline comment
     */
    `./pages/${
      page
      // inline comment
      /* comment2 */
    }`
  )
```

The expressions are matched with RegExp instead of parsing as AST for performance reason,
so you should only use it for simple cases as following:

1. relative path required
2. template literal required
3. no `)` in the `()` pair
4. extensions are optional

Additionally, the built-in functionality will be available in esbuild soon (maybe):
<https://github.com/evanw/esbuild/pull/2508#issue-1356677535>

## Sponsors

| 1stG                                                                                                                               | RxTS                                                                                                                               | UnTS                                                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| [![1stG Open Collective backers and sponsors](https://opencollective.com/1stG/organizations.svg)](https://opencollective.com/1stG) | [![RxTS Open Collective backers and sponsors](https://opencollective.com/rxts/organizations.svg)](https://opencollective.com/rxts) | [![UnTS Open Collective backers and sponsors](https://opencollective.com/unts/organizations.svg)](https://opencollective.com/unts) |

## Backers

[![Backers](https://raw.githubusercontent.com/1stG/static/master/sponsors.svg)](https://github.com/sponsors/JounQin)

| 1stG                                                                                                                             | RxTS                                                                                                                             | UnTS                                                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| [![1stG Open Collective backers and sponsors](https://opencollective.com/1stG/individuals.svg)](https://opencollective.com/1stG) | [![RxTS Open Collective backers and sponsors](https://opencollective.com/rxts/individuals.svg)](https://opencollective.com/rxts) | [![UnTS Open Collective backers and sponsors](https://opencollective.com/unts/individuals.svg)](https://opencollective.com/unts) |

## Changelog

Detailed changes for each release are documented in [CHANGELOG.md](./CHANGELOG.md).

## License

[MIT][] © [JounQin][]@[1stG.me][]

[1stg.me]: https://www.1stg.me
[jounqin]: https://GitHub.com/JounQin
[mit]: http://opensource.org/licenses/MIT
