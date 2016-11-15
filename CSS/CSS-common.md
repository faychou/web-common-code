# web-common-code
## CSS常用代码
### 一、清除浮动影响的clearfix几种写法
```CSS
.clearfix:after {
    content: '';
    display: block;
    clear: both;
    height: 0;
    visibility: hidden;
}
.clearfix {
    *zoom: 1;
}
```
<br/>
``` CSS
.clearfix {
  *zoom:1;
}
.clearfix:after {
  display:table;
  content:'';
  clear:both;
}
```
<br/>
``` CSS
// 同时加入:before以解决现代浏览器上边距折叠的问题
.clearfix:before,
.clearfix:after {
    display: table;
    content: " ";
}
.clearfix:after {
    clear: both;
}
.clearfix {
    *zoom: 1;
}
```

### 二、布局
1、两列布局（左边固定，右边自适应）<br/>
``` CSS
.left {
  width:200px;
  float:left;
}
.right {
  margin-left:200px;
}
```
2、两列布局（右边固定，左边自适应）<br/>
方法一：颠倒左右结构位置，采用上述方法；<br/><br/>
方法二：左侧自适应添加一个父元素
``` CSS
.wrap {
  width:100%;
  float:left;
}
.inner {
  margin-right:200px;
}
.right {
  width:200px;
  float:right;
  margin-left:-200px;
}
```

3、左右两列都自适应：
``` CSS
.left {
  float:left;
}
.right {
  display:table-cell;
  *display:inline-block;
}
```

3、三列布局（中间自适应，左右两边固定）-- 定位<br/>
``` html
<div class="left"></div>
<div class="center"></div>
<div class="right"></div>
```
<br/>
``` CSS
.left {
    width: 200px;
    position: absolute;
    left: 0;
    top: 0;
}
.center {
    margin: 0 200px;
}
.right {
    position: absolute;
    width: 200px;
    right: 0;
    top: 0;
}
```
4、三列布局（中间自适应，左右两边固定）-- 浮动<br/>
``` html
<div class="left"></div>
<div class="center">
    <div class="inner"></div>
</div>
<div class="right"></div>
```
<br/>
``` CSS
.left {            
    width: 200px;
    float: left;
}
.center {
    margin: 0 -200px;
    width: 100%;
    float: left;
}
.center .inner {
    margin: 0 200px;          
}
.right {            
    width: 200px;
    float: left;
}
```
5、三列布局（中间自适应，左右两边固定）方法三<br/>
``` html
<div class="container">
    <div class="center"></div>
    <div class="left"></div>
    <div class="right"></div>
</div>
```
<br/>
``` CSS
.container {
    padding: 0 200px 0 200px;
}
.center,.left,.right {
    position: relative;
    float: left;
}
.center {
    width: 100%;
}
.left {
    width: 200px;
    left: -200px;
    margin-left: -100%;
}
.right {
    width: 200px;
    margin-left: -200px;
    right: -200px;
}
```
### 三、定宽块元素居中
``` CSS
.auto {
  margin-left:auto;
  margin-right:auto;
}
```
### 四、单行文字溢出虚点显示
``` CSS
.ell{
  text-overflow:ellipsis;
  white-space:nowrap;
  overflow:hidden;
}
```
