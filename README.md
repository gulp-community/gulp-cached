[![Build Status](https://travis-ci.org/wearefractal/gulp-cached.png?branch=master)](https://travis-ci.org/wearefractal/gulp-cached)

[![NPM version](https://badge.fury.io/js/gulp-cached.png)](http://badge.fury.io/js/gulp-cached)

## Information

<table>
<tr> 
<td>Package</td><td>gulp-cached</td>
</tr>
<tr>
<td>Description</td>
<td>A simple in-memory file cache for gulp</td>
</tr>
<tr>
<td>Node Version</td>
<td>>= 0.9</td>
</tr>
</table>

## Usage

```javascript
var cache = require('gulp-cached');

gulp.task('lint', function(){
  return gulp.src("files/*.js")
    .pipe(cache('linting'))
    .pipe(jshint())
    .pipe(jshint.reporter())
});
```

### cache(cacheName[, opt])

Creates a new cache hash or uses an existing one.

Cache key = file.path + file.contents

If a file exists in the cache, it is ignored.

If a file doesn't exist in the cache, it is passed through as is and added to the cache.

The last cache for this path is cleared so if you modify a file to a, then to b, then back to a all 3 will be a cache miss.

#### Possible options

`optimizeMemory` - Uses md5 instead of storing the whole file contents. Better if you are worried about large files and their effect on memory consumption. Default is `false`

### Clearing the cache

#### Clearing the whole cache

```js
cache.caches = {};
```

#### Clearing a specific

```js
delete cache.caches['cache name yo'];
```

## LICENSE

(MIT License)

Copyright (c) 2014 Fractal <contact@wearefractal.com>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
