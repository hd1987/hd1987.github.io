---
title: gulpfile.js
date: 2016-10-10 23:23:48
tags: [js, nodejs]
---

gulpfile.js放置在根目录下，
启动命令'gulp serve'
> // 组件
> gulp
> browser-sync    // 自动刷新

<!-- more -->

```js
var gulp        = require('gulp');
var browserSync = require('browser-sync').create();
var reload      = browserSync.reload;

gulp.task('serve',function(){
  browserSync.init({
    server:{
      baseDir:'./'
    }
  });
  gulp.watch(['*/*.html','*/*/*.css']).on('change',browserSync.reload);
});
```


