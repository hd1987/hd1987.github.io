---
title: vue实现点击空白关闭弹窗，模拟下拉框Dropdown
date: 2022-12-20 22:54:12
categories:
  - Note
tags:
  - vue
---

方法一: 给外层容器定义一个阻止冒泡事件 `@click.stop`，则该容器内的点击不会传递到外层容器，所以全局监听不到该点击事件，在该容器内部点击不会触发点击函数。当弹框出现时，点击外部空白区域，弹框关闭。

方法二: 给外层容器设置一个 `ref="mian"`，当 visible为 true时，弹框出现。在该容器外点击 `this.$refs.main.$el.contains(e.target)`为 false，在容器内点击则为 true。

两种方法都需要组件挂载完毕，全局添加一个点击事件，组件注销前，将点击事件移除。

<!-- more -->

``` js
<template>
  <view @click.stop ref="main">
    <view @click.stop="handleOpenPopup">按钮</view>
    <view v-if="visible">弹出的内容</view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        visible: false,
      }
    },
    mounted() {
      // 组件挂载完毕，全局添加一个点击事件
      document.addEventListener('click', this.handleClose);
    },
    beforeDestroy() {
      // 组件销毁，全局移除一个点击事件
      document.removeEventListener('click', this.handleClose);
    },
    methods: {
      handleOpen() {
        // 显示隐藏内容
        if (!this.visible) this.visible = true;
      },
      handleClose(e) {
        if (this.visible) this.visible = false; // 方法一
        if (!this.$refs.main.$el.contains(e.target) && this.visible) this.visible = false; // 方法二
      }
    }
  }
</script>
```
