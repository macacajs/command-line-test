# command-line-test

[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Test coverage][coveralls-image]][coveralls-url]
[![node version][node-image]][node-url]
[![npm download][download-image]][download-url]

[npm-image]: https://img.shields.io/npm/v/command-line-test.svg?style=flat-square
[npm-url]: https://npmjs.org/package/command-line-test
[travis-image]: https://img.shields.io/travis/xudafeng/command-line-test.svg?style=flat-square
[travis-url]: https://travis-ci.org/xudafeng/command-line-test
[coveralls-image]: https://img.shields.io/coveralls/xudafeng/command-line-test.svg?style=flat-square
[coveralls-url]: https://coveralls.io/r/xudafeng/command-line-test?branch=master
[node-image]: https://img.shields.io/badge/node.js-%3E=_4-green.svg?style=flat-square
[node-url]: http://nodejs.org/download/
[download-image]: https://img.shields.io/npm/dm/command-line-test.svg?style=flat-square
[download-url]: https://npmjs.org/package/command-line-test

> command-line test tool for Node.js

## Installment

```bash
$ npm i command-line-test --save-dev
```

## Usage

`fork`, `spawn`, `exec`, `execFile` supported.

```javascript
const CliTest = require('command-line-test');

describe('test', function() {
  it('constructor should be ok', function() {
    CliTest.should.be.ok();
  });

  it('exec method should be ok with yeild', function *() {
    const cliTest = new CliTest();
    const res = yield cliTest.exec('cat package.json');
    /**
    * res return
    * {
    *   error,
    *   stdout,
    *   stderr
    * }
    */
    const _pkg = JSON.parse(res.stdout);
    pkg.name.should.be.equal(_pkg.name);
  });

  it('exec method should be ok with promise', function(done) {
    const cliTest1 = new CliTest();
    cliTest1.exec('cat package.json').then(res => {
      const _pkg = JSON.parse(res.stdout);
      pkg.name.should.be.equal(_pkg.name);
      done();
    });
  });

  it('exec method should be ok with callback', function(done) {
    const cliTest1 = new CliTest();
    cliTest1.exec('cat package.json', function(err, res) {
      const _pkg = JSON.parse(res.stdout);
      pkg.name.should.be.equal(_pkg.name);
      done();
    });
  });
});
```

## Sample

- [xudafeng/macaca-cli](//github.com/xudafeng/macaca-cli/)
- [xudafeng/app-inspector](//github.com/xudafeng/app-inspector/)
- [xudafeng/detect-port](//github.com/node-modules/detect-port/)
- [reliablejs/reliable-master](//github.com/reliablejs/reliable-master/)
- [reliablejs/reliable-macaca-slave](//github.com/reliablejs/reliable-macaca-slave)

## License

The MIT License (MIT)
