# Package Bundler

Bundle a Node.js module into a single file.

## Prerequisites

Depends on [`@vercel/ncc`](https://github.com/vercel/ncc), which should be installed globally:
```
$ npm i -g @vercel/ncc
```

## Installation

Download the `package-bundler` script and copy it to somewhere in your `$PATH`. Make sure it's executable:
```
$ chmod 755 /path/to/package-bundler
```

## How to use

#### Bundle a complete Node.js package
```
$ package-bundler lodash
```

#### Bundle some specific imports from a package
```
$ package-bundler lodash flattenDeep merge
```

## What it does

The script will create a temporary directory in which it will install the Node.js package to be bundled. Then it will write a small wrapper file that exports the package (or just the specific imports).

It will then run `ncc` against the wrapper file to bundle everything into a single file inside a directory named after the package. It will move this directory into your current working directory, and you should be able to load it from your main code.

## Limitations

* Not all packages can be bundled, especially ones that use dynamic `require` calls or packages like `require-all`.
* Does not support package versioning (`package@1.0.0`) yet, only the latest version of the package is bundled.
