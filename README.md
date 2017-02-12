# StdLib JavaScript (Web) Bindings

[Node](https://github.com/stdlib/lib-node) |
[Python](https://github.com/stdlib/lib-python) |
[Ruby](https://github.com/stdlib/lib-ruby) |
**Web**

Basic JavaScript (Web) bindings for StdLib service accession.

Used to interface with services built using [StdLib](https://stdlib.com) and
the [StdLib Command Line Tools](https://github.com/stdlib/lib).
You can utilize any service on StdLib without installing any additional
dependencies, and when you've deployed services to StdLib, you have a pre-built
web-based SDK --- for example;

```javascript
lib.yourUsername.hostStatus({name: 'Dolores Abernathy'}, (err, result) => {

  // handle result

});
```

To discover StdLib services, visit https://stdlib.com/search. To build a service,
get started with [the StdLib CLI tools](https://github.com/stdlib/lib).

## Installation

Simply save the `lib.js` file from this package anywhere in your web project,
and link it in the `<head>` element of an HTML file before any `<script>`s that
require it.

```html
<script src="path/to/lib.js"></script>
```

## Usage

```javascript
const lib = require('lib');

// [1]: Call "stdlib.reflect" function, the latest version, from StdLib
lib.stdlib.reflect(0, 1, {kwarg: 'value'}, (err, result) => {});

// [2]: Call "stdlib.reflect" function from StdLib, with "dev" environment
lib.stdlib.reflect['@dev'](0, 1, {kwarg: 'value'}, (err, result) => {});

// [3]: Call "stdlib.reflect" function from StdLib, with "release" environment
//      This is equivalent to (1)
lib.stdlib.reflect['@release'](0, 1, {kwarg: 'value'}, (err, result) => {});

// [4]: Call "stdlib.reflect" function from StdLib, with specific version
//      This is equivalent to (1)
lib.stdlib.reflect['@0.0.1'](0, 1, {kwarg: 'value'}, (err, result) => {});

// [5]: Call functions within the service (not just the defaultFunction)
//      This is equivalent to (1) when "main" is the default function
lib.stdlib.reflect.main(0, 1, {kwarg: 'value'}, (err, result) => {});

// Valid string composition from first object property only:
lib['stdlib.reflect'](0, 1, {kwarg: 'value'}, (err, result) => {});
lib['stdlib.reflect[@dev]'](0, 1, {kwarg: 'value'}, (err, result) => {});
lib['stdlib.reflect[@release]'](0, 1, {kwarg: 'value'}, (err, result) => {});
lib['stdlib.reflect[@0.0.1]'](0, 1, {kwarg: 'value'}, (err, result) => {});
lib['stdlib.reflect.main'](0, 1, {kwarg: 'value'}, (err, result) => {});
lib['stdlib.reflect[@dev].main'](0, 1, {kwarg: 'value'}, (err, result) => {});
lib['stdlib.reflect[@release].main'](0, 1, {kwarg: 'value'}, (err, result) => {});
lib['stdlib.reflect[@0.0.1].main'](0, 1, {kwarg: 'value'}, (err, result) => {});
```

### Local Usage

To use StdLib services locally (from within a StdLib function), use the
"string composition" method and begin your service path with a period;

```javascript
lib['.otherFunction']({key: 'X'}, (err, result) => {});
```

This functionality exists, so if needs be, you can directly interface with
other functions within a StdLib service when testing locally (i.e. MapReduce
  usage). Please note that **local functions always execute in the same context
  and thread as the caller**, meaning you *will not* get the scalability benefits
  of calling the function remotely, however **latency is significantly reduced**.

## Additional Information

To learn more about StdLib, visit [stdlib.com](https://stdlib.com) or read the
[StdLib CLI documentation on GitHub](https://github.com/stdlib/lib).

You can follow the development team on Twitter, [@polybit](https://twitter.com/polybit)

StdLib is &copy; 2016 - 2017 Polybit Inc.