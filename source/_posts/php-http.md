---
title: php发出http(post,get)请求
date: 2016-07-23 23:33:23
tags: php
---

web service model很多时候需要使用别的web service来建造自己的web service，这就需要到使用服务器端进行请求http操作，post或者get请求。

```php
/**
 * PHP发送请求获取数据
 * @param  [type] $url       [description]
 * @param  [type] $post_data [description]
 * @return [type] $result    [description]
 */
function send_post($url, $post_data) {
    $postdata = http_build_query($post_data);
    $options = array(
        'http' => array(
        'method' => 'POST',//or GET
        'header' => 'Content-type:application/x-www-form-urlencoded',
        'content' => $postdata,
        'timeout' => 15 * 60 // 超时时间（单位:s）
        )
    );
    $context = stream_context_create($options);
    $result = file_get_contents($url, false, $context);
    return $result;
}
```
以上是发送请求的函数，具体操作如下：
```php
//使用方法
$post_data = array(
    'username' => 'stclair2201',
    'password' => 'handan'
);
$result=send_post('http://localhost/ServiceProvider/index.php/Index/getService', $post_data);
```


