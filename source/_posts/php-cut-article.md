---
title: php提取文字并去除html标记，超出省略号表示
date: 2016-06-20 09:11:32
tags: php
---

```php
function cutArticle($data) {
    $data=strip_tags($data);//去除html标记
    $pattern = "/&[a-zA-Z]+;/";//去除特殊符号
    $data=preg_replace($pattern,'',$data);
    $data = mb_strimwidth($data,0,150,'....','UTF-8');
    return $data;
}
```


