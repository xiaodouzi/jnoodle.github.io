---
layout: post
title: 解决jquery mobile+phonegap页面切换闪屏问题
---

当jquery mobile在页面切换时出现闪屏，可以使用如下代码解决：

```javascript
    $(document).bind("mobileinit", function () {
        $.extend($.mobile, {
            defaultPageTransition : 'none'
        });

        $.mobile.defaultPageTransition = 'none';
        $.mobile.defaultDialogTransition = 'none';
    });
```