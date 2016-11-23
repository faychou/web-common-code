#web-common-code
## jQuery常用代码
### Tabs
``` javascript
var Cindex='';
$(document).ready(function(e) {
KyoTab($('.tl1 .Tabs'),$('.tc1 .Ctabs'));
KyoTab($('.tl2 .Tabs'),$('.tc2 .Ctabs'));
KyoTab($('.tl3 .Tabs'),$('.tc3 .Ctabs'));
});
function KyoTab(a,b){
a.hover(function(){
$(this).addClass('TabsBk').siblings().removeClass('TabsBk');
Cindex=$(this).index()-1;
b.eq(Cindex).removeClass('Thide').siblings().addClass('Thide');
});
};
```

### 下拉菜单
``` javascript
$(function() {
$("#nav ul li:has(ul)").hover(
function(){
$(this).children("ul").stop(true,true).slideDown(300);
//$(this).addClass("off");
},
function(){
$(this).children("ul").stop(true,true).slideUp("fast");
//$(this).removeClass("off");
}
);
})
```

### 条件加载jQuery
在使用jQuery时，为了兼容IE6、7、8，需要使用IE下的条件注释：
``` html
<!--[if lte IE 8]>
    <script type="text/javascript" src="jquery/jquery-1.11.1.js"></script>
<![endif]-->
<!--[if (gt IE 8)|!(IE)]><!-->
<script type="text/javascript" src="jquery/jquery-1.11.1.js"></script>
<!--<![endif]-->
```

### 头部与底部延迟加载动画效果
``` javascript
$(document).ready(function() {
$('#header')
.css({ 'top':-50 })
.delay(1000)
.animate({'top': 0}, 800);

$('#footer')
.css({ 'bottom':-15 })
.delay(1000)
.animate({'bottom': 0}, 800);   
});
```

### 禁用鼠标右键
``` javascript
$(document).ready(function() {
$(document).bind("contextmenu", function(e) {
return false;
});
});
```

### 让内容闪烁起来
``` javascript
$.fn.flash = function(color, duration) {
var current = this.css('color');
this.animate( {color: 'rgb(' + color + ')'}, duration / 2);
this.animate( {color: current}, duration / 2);
}
$('#someid').flash('255,0,0', 1000);
```

### 检测浏览器
``` javascript
// Safari
if( $.browser.safari )
{
//do something
}
//Above IE6
if ($.browser.msie && $.browser.version > 6 )
{
//do something
}
// IE6 and below
if ($.browser.msie && $.browser.version < 6 )  { //do something } // Firefox 2 and above if ($.browser.mozilla &amp;&amp; $.browser.version &gt;= "1.8" )
{
//do something
}
```

### 判断元素是否存在
``` javascript
if($("#someDiv").length) {
// yes it does, do something...
}
```

### 实时搜索(filter)下拉列表
``` javascript
$(function(){
//获取到下拉列表索引和内容对应表
var opts = $('#Select option').map(function(){
return [[this.value, $(this).text()]];
});

//绑定搜索框的keyup事件
$('#Text').keyup(function(){
//根据搜索框的内容生成一个忽略大小写的正则表达式
var rxp = new RegExp($('#Text').val(), 'i');
//先清空下拉列表
var optlist = $('#Select').empty();
//遍历对应表
opts.each(function(){
//如果内容与正则表达式匹配
if (rxp.test(this[1])) {
//那么加入到下拉列表中
optlist.append($('<option/>').attr('value', this[0]).text(this[1]));
}
});
});
});
```

### 弹性导航代码
``` javascript
$(function() {
var nav = $("#nav");
var navLine = nav.find(".nav-line");
var defLineW = nav.find(".current").width();
//获取当前位置偏移和宽度
var defLineLeft = nav.find(".current").position().left;
navLine.css({
left: defLineLeft,
width: defLineW
});
//定义当前位置
nav.find("li").hover(function() {
var index = $(this).index();
var curLineW = nav.find("li").eq(index).width();
var curLineLeft = $(this).position().left;
//alert(curLineLeft);
navLine.stop().animate({
left: curLineLeft,
width: curLineW
},
300);
},
function() {
navLine.stop().animate({
left: defLineLeft,
width: defLineW
},
300);
})
})
```

