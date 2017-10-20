# 代码库

## 返回顶部

```
// 返回顶部小插件
$.fn.backToTop = function (options) {

    var defaults = {
        topOffset: 300, // 开始显示返回顶部链接时与页面顶部的距离（像素）
        opacityOffset: 1200, // 开始变半透明时与页面顶部的距离（像素）
        duration: 700, // 返回顶部滚动的时间(ms),
        autoFade: false // 页面滚动到顶部的时候，返回顶部按钮隐藏
    }
    var opts = $.extend(defaults, options)

    var $elem = $(this) // 返回顶部链接

    if (opts.autoFade) {
        if ($(window).scrollTop() > opts.topOffset) {
            $elem.show()
        }
        // 隐藏或显示返回顶部链接
        $(window).scroll(function () {
            if ($(this).scrollTop() > opts.topOffset) {
                $elem.show()
            } else {
                $elem.hide()
            }

            if ($(this).scrollTop() > opts.opacityOffset) {
                // $elem.addClass('cd-fade-out');
            }
        })
    }

    // 平滑返回顶部
    $elem.on('click', function (event) {
        event.preventDefault()
        $('body,html').animate({
                scrollTop: 0
            },
            opts.duration
        )
    })

    return this
}
```

使用：

```
$('#to-top').backToTop()
```

版加班了