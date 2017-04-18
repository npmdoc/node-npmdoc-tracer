# npmdoc-tracer

#### api documentation for  [tracer (v0.8.7)](http://github.com/baryon/tracer)  [![npm package](https://img.shields.io/npm/v/npmdoc-tracer.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-tracer) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-tracer.svg)](https://travis-ci.org/npmdoc/node-npmdoc-tracer)

#### A powerful and customizable logging library for node.js. support color console with timestamp, line number, method name, file name and call stack. you can set transport to file, stream, database(ex: mongodb and clouddb, simpledb). keywords: log, logger, t

[![NPM](https://nodei.co/npm/tracer.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/tracer)

- [https://npmdoc.github.io/node-npmdoc-tracer/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-tracer/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-tracer/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-tracer/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-tracer/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-tracer/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "LI Long"
    },
    "bugs": {
        "url": "https://github.com/baryon/tracer/issues"
    },
    "dependencies": {
        "colors": "1.1.2",
        "dateformat": "1.0.12",
        "tinytim": "0.1.1"
    },
    "description": "A powerful and customizable logging library for node.js. support color console with timestamp, line number, method name, file name and call stack. you can set transport to file, stream, database(ex: mongodb and clouddb, simpledb). keywords: log, logger, t",
    "devDependencies": {
        "cli-color": "^1.1.0",
        "eslint": "^3.8.1",
        "expresso": "^0.9.2",
        "istanbul": "^0.4.5",
        "mongoskin": "0.3.0"
    },
    "directories": {},
    "dist": {
        "shasum": "d8e766de7ea8bb3ea28523b001691d3a95e3cd9c",
        "tarball": "https://registry.npmjs.org/tracer/-/tracer-0.8.7.tgz"
    },
    "engines": {
        "node": ">= 0.10.0"
    },
    "gitHead": "b01aa51c6f93e2194d816a9e290fd4b6733e2d1c",
    "homepage": "http://github.com/baryon/tracer",
    "keywords": [
        "log",
        "logger",
        "trace",
        "debug"
    ],
    "license": "MIT",
    "main": "./lib/index",
    "maintainers": [
        {
            "name": "baryon"
        }
    ],
    "name": "tracer",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git://github.com/baryon/tracer.git"
    },
    "scripts": {
        "lint": "eslint .",
        "posttest": "npm run lint",
        "posttest:coverage": "npm run lint",
        "test": "expresso test/*",
        "test:coverage": "istanbul cover expresso test/*.js"
    },
    "version": "0.8.7"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
