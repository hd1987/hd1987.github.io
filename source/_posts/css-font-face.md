---
title: 自定义字体 @font-face
date: 2017-04-28 16:47:20
tags: [css, sass]
---

```css
@font-face {
  font-family: 'MyWebFont';
  src: url('webfont.eot'); /* IE9 Compat Modes */
  src: url('webfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
       url('webfont.woff2') format('woff2'), /* Super Modern Browsers */
       url('webfont.woff') format('woff'), /* Pretty Modern Browsers */
       url('webfont.ttf')  format('truetype'), /* Safari, Android, iOS */
       url('webfont.svg#svgFontName') format('svg'); /* Legacy iOS */
}

body {
  font-family: 'MyWebFont', Fallback, sans-serif;
}
```

<!--more-->

# Practical Level of Browser Support

```css
@font-face {
  font-family: 'MyWebFont';
  src:  url('myfont.woff2') format('woff2'),
        url('myfont.woff') format('woff');
}
```

| Chrome | Safari | Firefox | Opera | IE | Android | iOS
| --- | --- | --- | --- | --- | --- | ---
| 5+ | 5.1+ | 3.6+ | 11.50+ | 9+ | 4.4+ | 5.1+

# Slightly Deeper Browser Support

```css 
@font-face {
  font-family: 'MyWebFont';
  src: url('myfont.woff2') format('woff2'),
       url('myfont.woff') format('woff'),
       url('myfont.ttf') format('truetype');
}
```

| Chrome | Safari | Firefox | Opera | IE | Android | iOS
| --- | --- | --- | --- | --- | --- | ---
| 3.5+ | 3+ | 3.5+ | 10.1+ | 9+ | 2.2+ | 4.3+

# Super Progressive Browser Support

```css
@font-face {
  font-family: 'MyWebFont';
  src: url('myfont.woff2') format('woff2');
}
```

| Chrome | Safari | Firefox | Opera | IE | Android | iOS
| --- | --- | --- | --- | --- | --- | ---
| 36+ | No | 35+ with flag | 23+ | No | 37 | No



