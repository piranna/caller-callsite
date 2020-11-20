# caller-callsite [![Build Status](https://travis-ci.org/sindresorhus/caller-callsite.svg?branch=master)](https://travis-ci.org/sindresorhus/caller-callsite)

> Get the [callsite](https://github.com/sindresorhus/callsites#api) of the caller function


## Install

```
$ npm install caller-callsite
```


## Usage

```js
// foo.js
const callerCallsite = require('caller-callsite');

module.exports = () => {
	console.log(callerCallsite().getFileName());
	//=> '/Users/sindresorhus/dev/unicorn/bar.js'
}
```

```js
// bar.js
const foo = require('./foo');
foo();
```


## API

### callerCallsite(options?)

Returns a [`callsite`](https://github.com/sindresorhus/callsites#api) object.

#### options

Type: `object`

##### depth

Type: `number`<br>
Default: `0`

The callsite depth, meaning how many levels we follow back on the stack trace.

For example:

```js
// foo.js
const callerCallsite = require('caller-callsite');

module.exports = () => {
	console.log(callerCallsite().getFileName());
	//=> '/Users/sindresorhus/dev/unicorn/foobar.js'
	console.log(callerCallsite({depth: 1}).getFileName());
	//=> '/Users/sindresorhus/dev/unicorn/bar.js'
	console.log(callerCallsite({depth: 2}).getFileName());
	//=> '/Users/sindresorhus/dev/unicorn/foo.js'
}
```

```js
// bar.js
const foo = require('./foo');

module.exports = () => {
	foo();
}
```

```js
// foobar.js
const bar = require('./bar');
bar();
```


---

<div align="center">
	<b>
		<a href="https://tidelift.com/subscription/pkg/npm-caller-callsite?utm_source=npm-caller-callsite&utm_medium=referral&utm_campaign=readme">Get professional support for this package with a Tidelift subscription</a>
	</b>
	<br>
	<sub>
		Tidelift helps make open source sustainable for maintainers while giving companies<br>assurances about security, maintenance, and licensing for their dependencies.
	</sub>
</div>
