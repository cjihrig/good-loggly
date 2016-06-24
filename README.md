# good-loggly

[![Current Version](https://img.shields.io/npm/v/good-loggly.svg)](https://www.npmjs.org/package/good-loggly)
[![Build Status via Travis CI](https://travis-ci.org/continuationlabs/good-loggly.svg?branch=master)](https://travis-ci.org/continuationlabs/good-loggly)
![Dependencies](http://img.shields.io/david/continuationlabs/good-loggly.svg)

[![belly-button-style](https://cdn.rawgit.com/continuationlabs/belly-button/master/badge.svg)](https://github.com/continuationlabs/belly-button)

Loggly broadcasting for Good.

**Credit:** This module was originally written and maintained by [fhemberger](https://github.com/fhemberger).

## Compatibility

- `good@7.x.x` is compatible with version >=3.x.x.
- `good@6.x.x` is compatible with version 1.x.x and 2.x.x.
- For older versions of `good`, use [v0.1.4](https://github.com/continuationlabs/good-loggly/releases/tag/v0.1.4).

## Usage

`good-loggly` is a [good](https://github.com/hapijs/good) reporter implementation to write [hapi](http://hapijs.com/) server events to Loggly.

Example integration:

```javascript
var Hapi = require('hapi');
var Good = require('good');
var GoodLoggly = require('good-loggly');

var server = new Hapi.Server();
var options = {
  reporters: [
    {
      reporter: GoodLoggly,
      events: { log: '*', request: '*'},
      config: {
        // Required
        token: 'YOUR LOGGLY TOKEN',
        subdomain: 'YOUR LOGGLY SUBDOMAIN',
        // Optional
        name: 'myapp',
        hostname: 'myapp.example.com',
        tags: ['global', 'tags', 'for', 'all', 'requests']
      }
    }
  ]
};

server.register({
  register: Good,
  options: options
}, function (err) {
  if (err) {
    return console.error(err);
  }
});
```
