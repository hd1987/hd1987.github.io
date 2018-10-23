---
title: checkbox 全选 反选
date: 2016-03-25 23:55:08
tags: js
---

``` js
//checkbox全选反选
function funCheckbox(){
    var intListAll, intListChecked;
    $(document).on("click","input[name='all']",function(){
        if($(this).is(":checked")){
            $("input[name='all']").prop("checked",true);
            $("input[name='list']").prop("checked",true);
        }else {
            $("input[name='all']").prop("checked",false);
            $("input[name='list']").prop("checked",false);
        }
    })
    intListAll = $("input[name='list']").length;//获取列表的个数
    $(document).on("click","input[name='list']",function(){
        intListChecked = $("input[name='list']:checked").length;
        if(intListChecked == intListAll){
            $("input[name='all']").prop("checked",true);
        }else {
            $("input[name='all']").prop("checked",false);
        }
    })
}
```
