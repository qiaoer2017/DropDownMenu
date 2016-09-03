## 使用HTML和CSS、JavaScript、jQuery三种方式实现下拉菜单

HTML结构:
```
<div id="menu">
    <ul>
        <li><a href="#">首页</a></li>
        <li><a href="#">课程大厅</a>
            <ul>
                <li><a href="#">HTML</a></li>
                <li><a href="#">CSS</a></li>
            </ul>
        </li>
        <li><a href="#">学习中心</a>
            <ul>
                <li><a href="#">视频学习</a></li>
                <li><a href="#">案例学习</a></li>
                <li><a href="#">交流平台</a></li>
            </ul>
        </li>
        <li><a href="#">经典案例</a></li>
        <li><a href="#">关于我们</a></li>
    </ul>
</div>

```
### 1. 使用HTML和CSS


```
#menu > ul > li:hover > ul {
    display: block;
}

#menu > ul > li > ul {
    display: none;
}
```

### 2. 使用JavaScript
```
window.onload = function () {
        var lists = document.getElementsByTagName("li");
        for (var i = 0; i < lists.length; i++) {
            lists[i].onmouseover = function () {
                var ul = this.getElementsByTagName("ul")[0];
                if (ul) {
                    ul.style.display = "block";
                }
            };
            lists[i].onmouseleave = function () {
                var ul = this.getElementsByTagName("ul")[0];
                if (ul) {
                    ul.style.display = "none";
                }
            };
        }
};
```

### 3. 使用jQuery
```
$(function () {
        var timer1;
        $("#menu > ul > li").mouseover(function () {
            var _self = $(this);
            timer = setTimeout(function () {
                _self.find('ul').show(100);
            }, 200);

        }).mouseleave(function () {
            var _self = $(this);
            clearTimeout(timer);
            _self.find('ul').hide(100);
        });
});
```