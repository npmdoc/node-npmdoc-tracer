# api documentation for  [tracer (v0.8.7)](http://github.com/baryon/tracer)  [![npm package](https://img.shields.io/npm/v/npmdoc-tracer.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-tracer) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-tracer.svg)](https://travis-ci.org/npmdoc/node-npmdoc-tracer)
#### A powerful and customizable logging library for node.js. support color console with timestamp, line number, method name, file name and call stack. you can set transport to file, stream, database(ex: mongodb and clouddb, simpledb). keywords: log, logger, t

[![NPM](https://nodei.co/npm/tracer.png?downloads=true)](https://www.npmjs.com/package/tracer)

[![apidoc](https://npmdoc.github.io/node-npmdoc-tracer/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-tracer_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-tracer/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-tracer/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-tracer/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "LI Long",
        "email": "lilong@gmail.com"
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
            "name": "baryon",
            "email": "lilong@gmail.com"
        }
    ],
    "name": "tracer",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module tracer](#apidoc.module.tracer)
1.  [function <span class="apidocSignatureSpan">tracer.</span>close ()](#apidoc.element.tracer.close)
1.  [function <span class="apidocSignatureSpan">tracer.</span>colorConsole (conf)](#apidoc.element.tracer.colorConsole)
1.  [function <span class="apidocSignatureSpan">tracer.</span>console ()](#apidoc.element.tracer.console)
1.  [function <span class="apidocSignatureSpan">tracer.</span>dailyfile (conf)](#apidoc.element.tracer.dailyfile)
1.  [function <span class="apidocSignatureSpan">tracer.</span>getLevel ()](#apidoc.element.tracer.getLevel)
1.  [function <span class="apidocSignatureSpan">tracer.</span>setLevel (level)](#apidoc.element.tracer.setLevel)
1.  object <span class="apidocSignatureSpan">tracer.</span>settings
1.  object <span class="apidocSignatureSpan">tracer.</span>utils

#### [module tracer.settings](#apidoc.module.tracer.settings)
1.  [function <span class="apidocSignatureSpan">tracer.settings.</span>close ()](#apidoc.element.tracer.settings.close)
1.  [function <span class="apidocSignatureSpan">tracer.settings.</span>getLevel ()](#apidoc.element.tracer.settings.getLevel)
1.  [function <span class="apidocSignatureSpan">tracer.settings.</span>setLevel (level)](#apidoc.element.tracer.settings.setLevel)
1.  object <span class="apidocSignatureSpan">tracer.</span>settings

#### [module tracer.utils](#apidoc.module.tracer.utils)
1.  [function <span class="apidocSignatureSpan">tracer.utils.</span>format (f)](#apidoc.element.tracer.utils.format)
1.  [function <span class="apidocSignatureSpan">tracer.utils.</span>union (obj, args)](#apidoc.element.tracer.utils.union)



# <a name="apidoc.module.tracer"></a>[module tracer](#apidoc.module.tracer)

#### <a name="apidoc.element.tracer.close"></a>[function <span class="apidocSignatureSpan">tracer.</span>close ()](#apidoc.element.tracer.close)
- description and source-code
```javascript
close = function (){
	settings.level = Number.MAX_VALUE;
}
```
- example usage
```shell
...
setLevel and close methods to dynamically change the log level.
these are global settings, affect all output that are created via tracer

'''javascript
var tracer = require('tracer');
tracer.setLevel(2); //or tracer.setLevel('debug');
//... ...
tracer.close();

'''

notice:
if you set level in initialize, you can't change more lower level than the initial level.

'''javascript
...
```

#### <a name="apidoc.element.tracer.colorConsole"></a>[function <span class="apidocSignatureSpan">tracer.</span>colorConsole (conf)](#apidoc.element.tracer.colorConsole)
- description and source-code
```javascript
colorConsole = function (conf) {
	return require('./console')({
		filters : {
			//log : do nothing
			trace : colors.magenta,
			debug : colors.cyan,
			info : colors.green,
			warn : colors.yellow,
			error : colors.red.bold
		}
	}, conf);
}
```
- example usage
```shell
...
var logger = require('tracer').console();
'''


Color Console

'''javascript
var logger = require('tracer').colorConsole();
'''

Set Output Level

'''javascript
var logger = require('tracer').colorConsole({level:'warn'});
'''
...
```

#### <a name="apidoc.element.tracer.console"></a>[function <span class="apidocSignatureSpan">tracer.</span>console ()](#apidoc.element.tracer.console)
- description and source-code
```javascript
console = function () {
	// default config
	var _config = {
		format : "{{timestamp}} <{{title}}> {{file}}:{{line}} ({{method}}) {{message}}",
		dateformat : "isoDateTime",
		preprocess : function(data) {
		},
		transport : function(data) {
			console.log(data.output);
		},
		filters : [],
		level : 'log',
		methods : [ 'log', 'trace', 'debug', 'info', 'warn', 'error' ],
		stackIndex : 0,		// get the specified index of stack as file information. It is userful for development package.
		inspectOpt : {
			showHidden : false, //if true then the object's non-enumerable properties will be shown too. Defaults to false
			depth : 2 //tells inspect how many times to recurse while formatting the object. This is useful for inspecting large complicated
 objects. Defaults to 2. To make it recurse indefinitely pass null.
		}
	};

	// union user's config and default
	_config = utils.union(_config, arguments);

	var _self = {};

	_config.format = Array.isArray(_config.format) ? _config.format
		: [ _config.format ];

	_config.filters = Array.isArray(_config.filters) ? _config.filters
		: [ _config.filters ];

	_config.transport = Array.isArray(_config.transport) ? _config.transport : [_config.transport];

	var fLen = _config.filters.length, lastFilter;
	if (fLen > 0)
		if (Object.prototype.toString.call(_config.filters[--fLen]) != '[object Function]') {
			lastFilter = _config.filters[fLen];
			_config.filters = _config.filters.slice(0, fLen);
		}

	if (typeof (_config.level) == 'string')
		_config.level = _config.methods.indexOf(_config.level);

	_config.methods.forEach(function(title, i) {
		if (i < _config.level)
			_self[title] = noop;
		else {
			var format = _config.format[0];
			if (_config.format.length === 2 && _config.format[1][title])
				format = _config.format[1][title];
			var needstack = /{{(method|path|line|pos|file)}}/i.test(format);

			var filters;
			if (lastFilter && lastFilter[title])
				filters = Array.isArray(lastFilter[title]) ? lastFilter[title]
					: [ lastFilter[title] ];
			else
				filters = _config.filters;

			// interface
			_self[title] = function() {
				return logMain(_config, i, title, format, filters, needstack, arguments);
			};
		}
	});

	return _self;
}
```
- example usage
```shell
...
Usage
-----
Add to your code:

Simple Console

'''javascript
var logger = require('tracer').console();
'''


Color Console

'''javascript
var logger = require('tracer').colorConsole();
...
```

#### <a name="apidoc.element.tracer.dailyfile"></a>[function <span class="apidocSignatureSpan">tracer.</span>dailyfile (conf)](#apidoc.element.tracer.dailyfile)
- description and source-code
```javascript
dailyfile = function (conf) {
    var _conf = {
        root: '.',
        logPathFormat: '{{root}}/{{prefix}}.{{date}}.log',
        splitFormat: 'yyyymmdd',
        allLogsFileName: false,
        maxLogFiles: 10
    };

    _conf = utils.union(_conf, [conf]);

    function LogFile(prefix, date) {
        this.date = date;
        this.path = tinytim.tim(_conf.logPathFormat, {root: _conf.root, prefix: prefix, date: date});
        spawnSync('mkdir', ['-p', _conf.root]);
        this.stream = fs.createWriteStream(this.path, {
            flags: "a",
            encoding: "utf8",
            mode: parseInt('0644', 8)
            // When engines node >= 4.0.0, following notation will be better:
            //mode: 0o644
        });
    }

    LogFile.prototype.write = function (str) {
        this.stream.write(str + "\n");
    };

    LogFile.prototype.destroy = function () {
        if (this.stream) {
            this.stream.end();
            this.stream.destroySoon();
            this.stream = null;
        }
    };

    var _logMap = {};

    function _push2File(str, title) {
        var logFile = _logMap[title], now = dateFormat(new Date(), _conf.splitFormat);
        if (logFile && logFile.date != now) {
            logFile.destroy();
            logFile = null;
        }
        if (!logFile) {
            logFile = _logMap[title] = new LogFile(title, now);
            spawn('find', [_conf.root, '-type', 'f', '-name', '*.log', '-mtime', '+' + _conf.maxLogFiles, '-exec', 'rm', '{}', '\;']);
        }
        logFile.write(str);
        if (_conf.allLogsFileName) {
            var allLogFile = _logMap.allLogFile, now = dateFormat(new Date(), _conf.splitFormat);
            if (allLogFile && allLogFile.date != now) {
                allLogFile.destroy();
                allLogFile = null;
            }
            if (!allLogFile) {
                allLogFile = _logMap.allLogFile = new LogFile(_conf.allLogsFileName, now);
                spawn('find', ['./', '-type', 'f', '-name', '*.log', '-mtime', '+' + _conf.maxLogFiles, '-exec', 'rm', '{}', '\;']);
            }
            allLogFile.write(str);
        }
    }

    function dailyFileTransport(data) {
        _push2File(data.output, data.title);
    }

    if (conf.transport) {
        conf.transport = Array.isArray(conf.transport) ? conf.transport : [conf.transport];
        conf.transport.push(dailyFileTransport)
    } else {
        conf.transport = [dailyFileTransport];
    }
    return require('./console')(conf);
}
```
- example usage
```shell
...
logger.info('hello %s %d',  'world', 123, {foo:'bar'});
logger.warn('hello %s %d %j', 'world', 123, {foo:'bar'});
logger.error('hello %s %d %j', 'world', 123, {foo:'bar'}, [1, 2, 3, 4], Object);
'''

### Daily Log
'''javascript
var logger = require('tracer').dailyfile({root:'.', maxLogFiles: 10, allLogsFileName: 'myAppName'});

logger.log('hello');
logger.trace('hello', 'world');
logger.debug('hello %s',  'world', 123);
logger.info('hello %s %d',  'world', 123, {foo:'bar'});
logger.warn('hello %s %d %j', 'world', 123, {foo:'bar'});
logger.error('hello %s %d %j', 'world', 123, {foo:'bar'}, [1, 2, 3, 4], Object);
...
```

#### <a name="apidoc.element.tracer.getLevel"></a>[function <span class="apidocSignatureSpan">tracer.</span>getLevel ()](#apidoc.element.tracer.getLevel)
- description and source-code
```javascript
getLevel = function (){
	return settings.level;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.tracer.setLevel"></a>[function <span class="apidocSignatureSpan">tracer.</span>setLevel (level)](#apidoc.element.tracer.setLevel)
- description and source-code
```javascript
setLevel = function (level){
	settings.level = level;
}
```
- example usage
```shell
...


setLevel and close methods to dynamically change the log level.
these are global settings, affect all output that are created via tracer

'''javascript
var tracer = require('tracer');
tracer.setLevel(2); //or tracer.setLevel('debug');
//... ...
tracer.close();

'''

notice:
if you set level in initialize, you can't change more lower level than the initial level.
...
```



# <a name="apidoc.module.tracer.settings"></a>[module tracer.settings](#apidoc.module.tracer.settings)

#### <a name="apidoc.element.tracer.settings.close"></a>[function <span class="apidocSignatureSpan">tracer.settings.</span>close ()](#apidoc.element.tracer.settings.close)
- description and source-code
```javascript
close = function (){
	settings.level = Number.MAX_VALUE;
}
```
- example usage
```shell
...
setLevel and close methods to dynamically change the log level.
these are global settings, affect all output that are created via tracer

'''javascript
var tracer = require('tracer');
tracer.setLevel(2); //or tracer.setLevel('debug');
//... ...
tracer.close();

'''

notice:
if you set level in initialize, you can't change more lower level than the initial level.

'''javascript
...
```

#### <a name="apidoc.element.tracer.settings.getLevel"></a>[function <span class="apidocSignatureSpan">tracer.settings.</span>getLevel ()](#apidoc.element.tracer.settings.getLevel)
- description and source-code
```javascript
getLevel = function (){
	return settings.level;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.tracer.settings.setLevel"></a>[function <span class="apidocSignatureSpan">tracer.settings.</span>setLevel (level)](#apidoc.element.tracer.settings.setLevel)
- description and source-code
```javascript
setLevel = function (level){
	settings.level = level;
}
```
- example usage
```shell
...


setLevel and close methods to dynamically change the log level.
these are global settings, affect all output that are created via tracer

'''javascript
var tracer = require('tracer');
tracer.setLevel(2); //or tracer.setLevel('debug');
//... ...
tracer.close();

'''

notice:
if you set level in initialize, you can't change more lower level than the initial level.
...
```



# <a name="apidoc.module.tracer.utils"></a>[module tracer.utils](#apidoc.module.tracer.utils)

#### <a name="apidoc.element.tracer.utils.format"></a>[function <span class="apidocSignatureSpan">tracer.utils.</span>format (f)](#apidoc.element.tracer.utils.format)
- description and source-code
```javascript
format = function (f) {
	var inspectOpt = this.inspectOpt;
	var args = arguments;
	var i = 0;

	if (typeof f !== 'string') {
		var objects = [];
		for (; i < args.length; i++) {
			objects.push(util.inspect(args[i], inspectOpt));
		}
		return objects.join(' ');
	}

	i = 1;
	var str = String(f).replace(formatRegExp, function(x) {
		switch (x) {
		case '%s':
			return String(args[i++]);
		case '%d':
			return Number(args[i++]);
		case '%j':
			try {
			    if (args[i] instanceof Error) {
				return JSON.stringify(args[i++], ['message', 'stack', 'type', 'name']);
        		    } else {
            			return JSON.stringify(args[i++]);
        		    }
			} catch(e) {
				return '[Circular]';
			}
		case '%t':
			return util.inspect(args[i++], inspectOpt);
		default:
			return x;
		}
	});
	for ( var len = args.length, x = args[i]; i < len; x = args[++i]) {
		if (x === null || typeof x !== 'object') {
			str += ' ' + x;
		} else {
			str += ' ' + util.inspect(x, inspectOpt);
		}
	}
	return str;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.tracer.utils.union"></a>[function <span class="apidocSignatureSpan">tracer.utils.</span>union (obj, args)](#apidoc.element.tracer.utils.union)
- description and source-code
```javascript
union = function (obj, args) {
	for (var i = 0, len = args.length; i < len; i += 1) {
		var source = args[i];
		for ( var prop in source) {
			obj[prop] = source[prop];
		}
	}
	return obj;
}
```
- example usage
```shell
...
		inspectOpt : {
			showHidden : false, //if true then the object's non-enumerable properties will be shown too. Defaults to false
			depth : 2 //tells inspect how many times to recurse while formatting the object. This is useful for inspecting large complicated
 objects. Defaults to 2. To make it recurse indefinitely pass null.
		}
	};

	// union user's config and default
	_config = utils.union(_config, arguments);

	var _self = {};

	_config.format = Array.isArray(_config.format) ? _config.format
		: [ _config.format ];

	_config.filters = Array.isArray(_config.filters) ? _config.filters
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
