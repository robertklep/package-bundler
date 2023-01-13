# Package Bundler

Bundle a Node.js module into a single file.

## Prerequisites

Depends on having a working, and recent, Node.js installation (including `npm`).

## Installation

Install the bundler script using NPM (requires Git to be installed as a CLI tool):
```
$ npm install -g https://github.com/robertklep/package-bundler
```

Alternatively, you can [download the code from Github as a ZIP file](https://github.com/robertklep/package-bundler/archive/refs/heads/main.zip) and run `npm install -g` from the `package-bundler-main` directory after unzipping the file.

## How to use

#### Bundle a complete Node.js package
```
$ package-bundler lodash
```

#### Bundle some specific imports from a package
```
$ package-bundler lodash flattenDeep merge
```

#### Bundle a specific package version
```
$ package-bundler lodash@4.0.0
```

## What it does

The script will create a temporary directory in which it will install the Node.js package to be bundled. Then it will write a small wrapper file that exports the package (or just the specific imports).

It will then run `ncc` against the wrapper file to bundle everything into a single file inside a directory named after the package. It will move this directory into your current working directory, and you should be able to load it from your main code.

## Limitations

* Not all packages can be bundled, especially ones that use dynamic `require` calls or packages like `require-all`.
