---
title: sass - Retinal屏border显示1px
date: 2016-12-06 15:55:26
tags: [css, sass]
---

```css
@mixin border($top, $right, $bottom, $left, $color:#f00) {
  content: " ";
  position: absolute;
  top: $top;
  right: $right;
  bottom: $bottom;
  left: $left;
  color: $color;
  $position: '';
  $transform-origin: '';
  $scale: '';
  @if $top == 'auto' or $bottom == 'auto' {
    height: 1px;
    $scale: 1, .5;
  }
  @else if $left == 'auto' or $right == 'auto' {
    width: 1px;
    $scale: .5, 1;
  }
  @if $top == 'auto' {
    $position: bottom;
    $transform-origin: 0 100%;
  }
  @else if $right == 'auto' {
    $position: left;
    $transform-origin: 0 0;
  }
  @else if $bottom == 'auto' {
    $position: top;
    $transform-origin: 0 0;
  }
  @else if $left == 'auto' {
    $position: right;
    $transform-origin: 100% 0;
  }
  border-#{$position} : 1px solid $color;
  -webkit-transform-origin: $transform-origin;
  transform-origin: $transform-origin;
  -webkit-transform: scale($scale);
  transform: scale($scale);
  z-index: 1;
}
.demo {
  position: relative;
  &:before {
    @include border(0, 0, auto, 0, #666);  // top, right, bottom, left, color
  }
}
```

