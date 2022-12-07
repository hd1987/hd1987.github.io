---
title: 微信H5自定义分享在ios下失效的问题
date: 2022-06-06 10:29:03
categories:
  - Note
tags:
  - wechat
  - ios
---

**ios分享失效，表现为不显示缩略图，自定义url不正确，无法获取title等**

> * IOS：每次切换路由，SPA的url是不会变的，发起签名请求的url参数必须是当前页面的url(就是最初进入页面时的url)
> * Android：每次切换路由，SPA的url是会变的，发起签名请求的url参数必须是当前页面的url(不是最初进入页面时的)

<!--more-->

**如果你配置了微信分享，但没有给值。Android：会取默认值有时会有图标。IOS：肯定没有图标**

**如果想实现自定义：**

ios要在App.vue中获取并缓存该url，android不需要。需要动态判断设备系统类型 (uniapp示例)
```js
//在App.vue中获取并缓存
uni.setStorageSync('url',window.location.href)

//在传给后端url获取返回参数配置wx.config前，加动态判断
let url = uni.getSystemInfoSync().platform === 'ios' ? uni.getStorageSync('url') : window.location.href
```
