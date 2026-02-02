# Bun

+ [Install](#install)
+ [Bundler](#bundler)

## Install
`Bun` can be installed for both `macOS` and `Windows`:

```shell
# macOS
$ curl -fsSL https://bun.sh/install | bash

# Windows
$ powershell -c "irm bun.sh/install.ps1 | iex"
```

`Bun` can also be installed as a `package` using `npm` or with `Homebrew`:

```shell
# Installed using npm
$ npm install -g bun

# Installed using Homebrew
$ brew install oven-sh/bun/bun
```

Once installed, restart the terminal and check the version:

```shell
$ bun --version
```

## Bundler
A bundler is designed to take multiple files and bundle them into a single file, or reduced number of files, to reduce the number of requests needed. It can also be used to reduce the file size to improve performance of the application and convert modern `JavaScript` or `TypeScript` code into older syntax for compatibilities with different browsers.

`Bun` has a native `bundler` for: `JavaScript`, `TypeScript`, `JSX` and more. This bundler can be used using the following terminal command:

```shell
$ bun build
```

This command would bundle a single `JavaScript` file from within a `src` directory into a `dist` directory:

```shell
$ bun build ./src/index.js --outfile ./dist/app.js
```

If the output file needs `minification`, use the `--minify` flag:

```shell
$ bun build ./src/index.js --outfile ./dist/app.min.js --minify
```

To bundle multiple files:

```shell
$ bun build src/*.js --outdir dist --minify
```
