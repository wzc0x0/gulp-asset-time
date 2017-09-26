## gulp-asset-time

a plugin for gulp.js to replace file's name by adding current time  
fork from [gulp-asset-rev](https://github.com/hellopao/gulp_plugin/tree/master/gulp-asset-rev)

## Installation

```bash
npm install gulp-asset-time -D
```

## Usage

```js
var gulp = require('gulp');
var assetRev = require('gulp-asset-time');

gulp.task('rev',function() {
    gulp.src("./test/test.html")
        .pipe(assetRev())
        .pipe(gulp.dest('./'));
});
```


```js
var gulp = require('gulp');
var assetRev = require('./index.js');

gulp.task('rev',['revCss'],function() {
    gulp.src("./test/test.html")
        .pipe(assetRev())
        .pipe(gulp.dest('./dest'));
});

gulp.task('revCss',function () {
    return gulp.src('./test/styles/test.css')
        .pipe(assetRev())
        .pipe(gulp.dest('./dest/styles/'))
});
gulp.task('default',['rev']);
```

### before: test.css
```css
body{background:url('../images/bg.png')}
```

### after: test.css
```css
body{background:url("../images/bg?v=19700101010.png"}
```
### before: test.html
```html
<html lang="en">
<head>
    <meta charset="utf-8"/>
    <title></title>
    <link rel="stylesheet" href="./styles/test.css" type="text/css" />
</head>
<body>
    <div>
        <img src="./images/test.png" />
    </div>
    <script src="./scripts/test.js" type="text/javascript"></script>
</body>
</html>
```
### after: test.html

```html
<html lang="en">
<head>
    <meta charset="utf-8"/>
    <title></title>
    <link rel="stylesheet" href="./styles/test?v=19700101010.css" type="text/css" />
</head>
<body>
    <div>
        <img src="./images/test?v=19700101010.png" />
    </div>
    <script src="./scripts/test?v=19700101010.js" type="text/javascript"></script>
</body>
</html>
```



