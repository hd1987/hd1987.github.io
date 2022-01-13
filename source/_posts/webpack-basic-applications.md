---
title: webpack4 基本设置应用示例 (Nodejs -v10)
date: 2018-05-31 11:40:24
tags: [npm, webpack]
---

## 目录结构

    dist
    |  font
    |  |  ...
    |  images
    |  |  ...
    |  js
    |  |  index.js
    |  css
    |  |  styles.css
    node_modules
    src
    |  font
    |  |  ...
    |  images
    |  |  ...
    |  js
    |  |  module
    |  |  |  loading.js
    |  |  |  ...
    |  |  index.js
    |  scss
    |  |  base
    |  |  |  ...
    |  |  function
    |  |  |  ...
    |  |  layout
    |  |  |  ...
    |  |  mixin
    |  |  |  ...
    |  |  _variables.scss
    |  |  styles.scss
    package.json
    webpack.config.js
    webpack.config.entry.js（把需要编译的多个js入口单独写配置文件）

## 使用方法

`npm install` 安装命令（每个项目仅需执行一次）
`npm run-script build` 编译一次，并压缩文件
`npm start` 编译并启动监听

<!-- more -->

## package.json

```json
{
  "name": "front-env-webpack4",
  "description": "",
  "version": "1.0.0",
  "private": true,
  "license": "ISC",
  "scripts": {
    "build": "webpack -p --progress --mode production",
    "start": "webpack -w --progress --mode development"
  },
  "devDependencies": {
    "ajv": "^6.5.2",
    "babel-core": "^6.26.3",
    "babel-loader": "^7.1.5",
    "babel-preset-env": "^1.7.0",
    "css-loader": "^1.0.0",
    "extract-text-webpack-plugin": "^4.0.0-beta.0",
    "file-loader": "^1.1.11",
    "node-sass": "^4.9.2",
    "optimize-css-assets-webpack-plugin": "^5.0.0",
    "postcss-loader": "^2.1.6",
    "sass-loader": "^7.0.3",
    "style-loader": "^0.21.0",
    "uglifyjs-webpack-plugin": "^1.2.7",
    "webpack": "^4.16.1",
    "webpack-cli": "^3.0.8"
  },
  "dependencies": {}
}

```

## webpack.config.js

```js
var path = require('path')
var ExtractTextPlugin = require('extract-text-webpack-plugin')

module.exports = {
  entry: './src/js/index.js',
  // entry: require('./webpack.config.entry'),
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'js/index.js'
    // filename: 'js/[name].js'
  },
  resolve: {
    extensions: ['*', '.js']
  },
  module: {
    rules: [
      {
        test: /\.js?$/,
        include: path.resolve(__dirname, 'src/js'),
        use: [
          {
            loader: 'babel-loader',
            options: {
              presets: ['env']
            }
          }
        ]
      },
      {
        test: /\.(scss|css)$/,
        loader: ExtractTextPlugin.extract({
          fallback: 'style-loader',
          publicPath: '../',
          use: [
            {
              loader: 'css-loader',
              options: {
                minimize: true
              }
            },
            { loader: 'sass-loader' },
            {
              loader: 'postcss-loader',
              options: {
                options: {}
              }
            }
          ]
        })
      },
      {
        test: /\.(svg|png|jpe?g)(\?\S*)?$/,
        use: [
          {
            loader: 'file-loader?name=images/[name].[ext]'
          }
        ]
      },
      {
        test: /\.(eot|svg|ttf|woff|woff2)$/,
        exclude: [/images/],
        use: [
          {
            loader: 'file-loader?name=fonts/[name].[ext]'
          }
        ]
      }
    ]
  },
  plugins: [
    new ExtractTextPlugin('css/styles.css')
    // new ExtractTextPlugin('css/[name].css')
  ]

}

```

## webpack.config.entry.js

```js
var path = require('path');

module.exports = {
  'index': path.resolve(__dirname, './src/js/index.js'),
  // ...
}

```

## index.js

```js
require('./../scss/style.scss');  // modify the style.scss

import { loading } from './module/loading';

window.onload = function () {

  // loading
  loading();

};
```

## loading.js

```js
export let loading = () => {

  (function ($) {
    'use strict';

    let loadingHTML = `<div class="loading"></div>`;

    $(document).ajaxStart(function() {
      $('body').append(loadingHTML);
    })

    $(document).ajaxStop(function() {
      $('.loading').remove();
    })
    
  })(jQuery);
}
```
