# Level

## Why this fork?

This fork is to provide [`level-party`](https://github.com/substack/level-party) a version of [`level`](https://github.com/Level/level) that installs on Node.js v10+ without going through major upgrades.

The module `level-party` depends on `level v1`, which will fail to install on Node.js v10+ due to it's dependecy on [`leveldown v1`].

When bumping to `level v2+`, key and value encodings are moved out of `levelup` and into [`encoding-down`](https://github.com/Level/encoding-down). This causes tests to fail in `level-party`.

This is a fork of `level v1`, but updates to use `leveldown v2`. This continues to keep tests passing on `level-party`, and enables it work on Node.js v10+

<img alt="LevelDB Logo" height="100" src="http://leveldb.org/img/logo.svg">

**Fast & simple storage - a Node.js-style LevelDB wrapper**

[![Build Status](https://secure.travis-ci.org/Level/level.png)](http://travis-ci.org/Level/level)
[![dependencies](https://david-dm.org/Level/level.svg)](https://david-dm.org/level/level)

[![NPM](https://nodei.co/npm/level.png?stars&downloads&downloadRank)](https://nodei.co/npm/level/) [![NPM](https://nodei.co/npm-dl/level.png?months=6&height=3)](https://nodei.co/npm/level/)

This is a convenience package that bundles the current release of **[LevelUP](https://github.com/level/levelup)** and **[LevelDOWN](https://github.com/level/leveldown)** and exposes LevelUP on its export.

Use this package to avoid having to explicitly install LevelDOWN when you just want plain old LevelDB from LevelUP.

```js
var level = require("level");

// 1) Create our database, supply location and options.
//    This will create or open the underlying LevelDB store.
var db = level("./mydb");

// 2) put a key & value
db.put("name", "Level", function(err) {
  if (err) return console.log("Ooops!", err); // some kind of I/O error

  // 3) fetch by key
  db.get("name", function(err, value) {
    if (err) return console.log("Ooops!", err); // likely the key was not found

    // ta da!
    console.log("name=" + value);
  });
});
```

See **[LevelUP](https://github.com/rvagg/node-levelup)** and **[LevelDOWN](https://github.com/rvagg/node-leveldown)** for more details.

<a name="contributing"></a>
Contributing

---

Level is an **OPEN Open Source Project**. This means that:

> Individuals making significant and valuable contributions are given commit-access to the project to contribute as they see fit. This project is more like an open wiki than a standard guarded open source project.

See the [`CONTRIBUTING.md`](https://github.com/Level/community/blob/master/CONTRIBUTING.md) file for more details.

<a name="license"></a>
License &amp; Copyright

---

Copyright (c) 2012-2017 **Level** [contributors](https://github.com/level/community#contributors).

Level is licensed under the MIT license. All rights not explicitly granted in the MIT license are reserved. See the included `LICENSE.md` file for more details.
