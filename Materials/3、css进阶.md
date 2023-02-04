# CSS进阶 八点正式上课

[TOC]

## 盒子模型——边框

```css
CSS盒模型本质上是一个盒子，封装周围的HTML元素，它包括：边距，边框，填充，和实际内容。盒模型允许我们在其它元素和周围元素边框之间的空间放置元素。
所有的文档元素（标签）都会生成一个矩形框，我们成为元素框，它描述了一个文档元素再网页布局汇总所占的位置大小。因此，每个盒子除了有自己大小和位置外，还影响着其他盒子的大小和位置。
```

```css
盒子模型特性：
      每个盒子都有：边界、边框、填充、内容 4个属性；
      每个属性都包括4个部分：上、右、下、左。属性的4部分可以同时设置，也可以分别设置。
```

```css
Margin(外边距) - 清除边框外的区域，外边距是透明的。
Border(边框) - 围绕在内边距和内容外的边框。
Padding(内边距) - 清除内容周围的区域，内边距是透明的。
Content(内容) - 盒子的内容，显示文本和图像。
```

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>CSS进阶</title>
  <style>
    div{
      width: 200px;
      height: 200px;
      /*复合样式：边框粗细1px，实线，红色线*/
      /*border: 1px solid red;*/

      /*边框颜色*/
      /*border-color: green;*/

      /*!*边框宽度*!*/
      /*border-width: 5px;*/

      /*!*边框样式*!*/
      /*border-style: solid;*/
      
      /*上边框-：1px 实线 红色*/
      border-top: 1px solid red;
      /*右边框-：2px 虚线 绿色*/
      border-right: 2px dashed green;
      /*下边框-：3px 点线 蓝色*/
      border-bottom: 3px dotted blue;
      /*左边框-：4px 双线 分红色*/
      border-left: 4px double pink;
    }
  </style>
</head>
<body>
<div></div>

</body>
</html>
```

## 盒子模型——内边距

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>CSS进阶</title>
  <style>
    div{
      width: 200px;
      height: 200px;
      border: 1px solid red;

      /*复合样式：可以设置4个值，3个值，2个值，1个值*/
      padding: 50px 60px 70px 80px;

      /*内边距，上下左右，设置属性，会把盒子撑大,不能设置负数，负数就还原初始状态*/
      /*padding-top: 100px;*/
      /*padding-right: 100px;*/
      /*padding-bottom: 100px;*/
      /*padding-left: 100px;*/
    }
  </style>
</head>
<body>
<div>我是内容</div>

</body>
</html>
```

## 盒子模型——外边距

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>CSS进阶</title>
  <style>
    div{
      width: 200px;
      height: 200px;
    }
    .d1{
      border: 1px solid red;

      /*外边距，可以设置负数，不会撑大盒子*/
      /*margin-top: 50px;*/
      /*margin-right: 50px;*/
      /*margin-bottom: 50px;*/
      /*margin-left: 50px;*/

      /*复合样式,可以设置4个值，3个值，2个值，1个值*/
      margin: 50px 60px 70px 80px;
      
      /*融合行内于块级，用通俗的话讲，就是不独占一行的块级元素*/
      display:inline-block;

    }
    .d2{
      border: 2px solid blue;
      display:inline-block;
    }
  </style>
</head>
<body>
<div class="d1"></div>
<div class="d2"></div>
</body>
</html>
```

## 重置样式

```css
每个浏览器都有一些自带的或者共有的默认样式，或造成一些布局上的困扰，css  reset的作用就是重置这些默认样式，使样式表现一致；

为了让页面获得浏览器跨浏览器的兼容性，需要用重置文件css代码覆盖浏览器默认的样式来统一样式。
```

```css
https://meyerweb.com/eric/tools/css/reset/
```

```css
新建css文件，把网页里面的重置样式复制进去
再使用link标签导入该样式：
<link rel="stylesheet" href="../css/reset.css">
```

## 浮动

```css
CSS 的 Float（浮动），会使元素向左或向右移动，其周围的元素也会重新排列。
浮动一般是用于图像，但它在布局时一样非常有用。
```

```css
元素怎样浮动:
元素的水平方向浮动，意味着元素只能左右移动而不能上下移动。
一个浮动元素会尽量向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。
浮动元素之后的元素将围绕它。
浮动元素之前的元素将不会受到影响。
```

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>CSS进阶</title>
  <style>
    .div1{
      width: 100px;
      height: 100px;
      background: red;
      /*第一种：右浮动*/
      /*float: right;*/
      /*第二种：左浮动*/
      /*float: left;*/
        
      /*第三种，站一排*/
      float: left;
    }
    .div2{width: 100px;height: 100px;background: pink;
      /*第三种，站一排*/
      float: left;
    }
    .div3{width: 100px;height: 100px;background: blue;
      /*第三种，站一排*/
      float: left;
    }
  </style>
</head>
<body>
  <div>
    <div class="div1"></div>
    <div class="div2"></div>
    <div class="div3"></div>
  </div>
</body>
</html>
```

### 问题：高度坍塌

```
1，正常情况看高度；
2，都设置左浮动；
3，站一排后看高度为0了。
```

### 三种解决办法：

#### 1，父元素设置：

```css
style中添加一个类元素：（然看查看网页检查高度）
  <style>
    .div4{
      /*超出部分隐藏*/
      overflow: hidden;
    }
  </style>
  
<body>
  	<div class="div4"></div>
    <div class="div1"></div>
    <div class="div2"></div>
    <div class="div3"></div>
</body>
```

#### 2，添加一个空div

```css
  <style>
	.div5{width: 100px;height: 100px;}
  </style>
<body>
  <div>
    <div class="div1"></div>
    <div class="div2"></div>
    <div class="div3"></div>
    <!--添加一个空盒子-->
    <div class="div5"></div>
  </div>
</body>

布局过多，就需要很多的空盒子，不建议使用
```

#### 3，使用伪元素

```css
原理：给最后一个盒子添加一个元素，把盒子撑起来

  <style>
		.div4:after{				# after:之后
      		content: " ";			# content内容
      		display: block;			# display显示，block块
      		clear: both;			# clear清空，both左右浮动
    		}
  </style>
<body>
  <div class="div4">
    <div class="div1"></div>
    <div class="div2"></div>
    <div class="div3"></div>
  </div>
</body>
```

### 定位

```css
元素可以使用的顶部，底部，左侧和右侧属性定位。然而，这些属性无法工作，除非是先设定position属性。他们也有不同的工作方式，这取决于定位方法。
```

#### static 定位

```css
HTML 元素的默认值，即没有定位，遵循正常的文档流对象。
静态定位的元素不会受到 top, bottom, left, right影响。
```

```css
<style>
  .moren{position: static; border: 3px solid #73AD21;}
</style>
<body>
<h2>标题2</h2>
<p>使用 position: static; 定位的元素，无特殊定位，遵循正常的文档流对象:</p>
<div class="moren">
该元素使用了 position: static;
</div>
</body>
```

#### fixed 定位

```css
元素的位置相对于浏览器窗口是固定位置。

即使窗口是滚动的它也不会移动：
```

```css
<style>
.guding {
  position:fixed;
  width: 100px;
  height: 100px;
  background:deepskyblue;
  top:30px;
  left: 50px;
}
</style>
<body>
<div class="guding"></div>

<div style="width: 100px;height: 100px;border: 1px solid red"></div>
<div style="width: 100px;height: 100px;border: 1px solid red"></div>
<div style="width: 100px;height: 100px;border: 1px solid red"></div>
<div style="width: 100px;height: 100px;border: 1px solid red"></div>
<div style="width: 100px;height: 100px;border: 1px solid red"></div>
<div style="width: 100px;height: 100px;border: 1px solid red"></div>
<div style="width: 100px;height: 100px;border: 1px solid red"></div>
<div style="width: 100px;height: 100px;border: 1px solid red"></div>
<div style="width: 100px;height: 100px;border: 1px solid red"></div>
<div style="width: 100px;height: 100px;border: 1px solid red"></div>
</body>
```

#### relative 定位

```css
相对定位元素的定位是相对其正常位置。
```

```css
<style>
h2.pos_left
{
	position:relative;
	left:-20px;
}

h2.pos_right
{
	position:relative;
	left:20px;
}
</style>
<body>
<h2>正常位置的标题</h2>
<h2 class="pos_left">这个标题相对于其正常位置向左移动</h2>
<h2 class="pos_right">这个标题相对于其正常位置向右移动</h2>
<p>相对定位会按照元素的原始位置对该元素进行移动。</p>
<p>样式 "left:-20px" 从元素的原始左侧位置减去 20 像素。</p>
<p>样式 "left:20px" 向元素的原始左侧位置增加 20 像素。</p>
</body>
```

**移动相对定位元素，但它原本所占的空间不会改变。**

```css
<style>
h2.pos_top
{
	position:relative;
	top:-50px;
}
</style>
<body>
<h2>这是一个没有定位的标题</h2>
<h2 class="pos_top">这个标题是根据其正常位置向上移动</h2>
<p><b>注意:</b> 即使相对定位元素的内容是移动,预留空间的元素仍保存在正常流动。</p>
</body>
```

**相对定位元素经常被用来作为绝对定位元素的容器块**。

#### absolute 定位

```
绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那么它的位置相对于<html>:
```

```css
<style>
h2
{
	position:absolute;
	left:100px;
	top:150px;
}
</style>
<body>
<h2>这是一个绝对定位了的标题</h2>
<p>用绝对定位,一个元素可以放在页面上的任何位置。标题下面放置距离左边的页面100 px和距离页面的顶部150 px的元素。.</p>
</body>
```

**absolute 定位使元素的位置与文档流无关，因此不占据空间。**

**absolute 定位的元素和其他元素重叠。**

#### sticky 定位

```css
sticky 英文字面意思是粘，粘贴，所以可以把它称之为粘性定位。

position: sticky; 基于用户的滚动位置来定位。

粘性定位的元素是依赖于用户的滚动，在 position:relative 与 position:fixed 定位之间切换。

它的行为就像 position:relative; 而当页面滚动超出目标区域时，它的表现就像 position:fixed;，它会固定在目标位置。

元素定位表现为在跨越特定阈值前为相对定位，之后为固定定位。

这个特定阈值指的是 top, right, bottom 或 left 之一，换言之，指定 top, right, bottom 或 left 四个阈值其中之一，才可使粘性定位生效。否则其行为与相对定位相同。

注意: Internet Explorer, Edge 15 及更早 IE 版本不支持 sticky 定位。 Safari 需要使用 -webkit- prefix (查看以下实例)。
```

```css
<style>
div.sticky {
  position: -webkit-sticky;
  position: sticky;
  top: 0;
  padding: 5px;
  background-color: #cae8ca;
  border: 2px solid #4CAF50;
}
</style>

<body>
<p>尝试滚动页面。</p>
<p>注意: IE/Edge 15 及更早 IE 版本不支持 sticky 属性。</p>
<div class="sticky">我是粘性定位!</div>
<div style="padding-bottom:2000px">
  <p>滚动我</p>
  <p>来回滚动我</p>
  <p>滚动我</p>
  <p>来回滚动我</p>
  <p>滚动我</p>
  <p>来回滚动我</p>
</div>
</body>
```

#### 重叠的元素

```css
元素的定位与文档流无关，所以它们可以覆盖页面上的其它元素

z-index属性指定了一个元素的堆叠顺序（哪个元素应该放在前面，或后面）

一个元素可以有正数或负数的堆叠顺序：
```

```css
代码演示;
<style>
img{
	position:absolute;
	left:0px;
	top:0px;
	z-index:-1;
}
</style>
<body>
<h1>这是标题一</h1>
<img src="图片" />
<p>由于图像的 z-index 是 -1，因此它在文本的后面出现。</p>
</body>
```

**具有更高堆叠顺序的元素总是在较低的堆叠顺序元素的前面。**

**注意： 如果两个定位元素重叠，没有指定z - index，最后定位在HTML代码中的元素将被显示在最前面。**

```css
值					描述
auto			默认。堆叠顺序与父元素相等。
number			设置元素的堆叠顺序。
inherit			规定应该从父元素继承 z-index 属性的值。
```





#### 案例:滚动条显示溢出的内容

```css
<style>
div.ex1 {
    background-color: lightblue;
    width: 110px;
    height: 110px;
    overflow: scroll;
}

div.ex2 {
    background-color: lightblue;
    width: 110px;
    height: 110px;
    overflow: hidden;
}

div.ex3 {
    background-color: lightblue;
    width: 110px;
    height: 110px;
    overflow: auto;
}

div.ex4 {
    background-color: lightblue;
    width: 110px;
    height: 110px;
    overflow: visible;
}
</style>

<body>
<h1>overflow 属性</h1>
<p>如果元素中的内容超出了给定的宽度和高度属性，overflow 属性可以确定是否显示滚动条等行为。</p>

<h2>overflow: scroll:</h2>
<div class="ex1">图灵课堂 -- 给学员一个更好的未来</div>

<h2>overflow: hidden:</h2>
<div class="ex2">图灵课堂 -- 给学员一个更好的未来</div>

<h2>overflow: auto:</h2>
<div class="ex3">图灵课堂 -- 给学员一个更好的未来</div>

<h2>overflow: visible (默认):</h2>
<div class="ex4">图灵课堂 -- 给学员一个更好的未来</div>
</body>
```

#### 案例:更改鼠标光标：

```css
<body>
<p>请把鼠标移动到单词上，可以看到鼠标指针发生变化：</p>
<span style="cursor:auto">auto</span><br>
<span style="cursor:crosshair">crosshair</span><br>
<span style="cursor:default">default</span><br>
<span style="cursor:e-resize">e-resize</span><br>
<span style="cursor:help">help</span><br>
<span style="cursor:move">move</span><br>
<span style="cursor:n-resize">n-resize</span><br>
<span style="cursor:ne-resize">ne-resize</span><br>
<span style="cursor:nw-resize">nw-resize</span><br>
<span style="cursor:pointer">pointer</span><br>
<span style="cursor:progress">progress</span><br>
<span style="cursor:s-resize">s-resize</span><br>
<span style="cursor:se-resize">se-resize</span><br>
<span style="cursor:sw-resize">sw-resize</span><br>
<span style="cursor:text">text</span><br>
<span style="cursor:w-resize">w-resize</span><br>
<span style="cursor:wait">wait</span><br>
</body>
</html>
```

## CSS作业

### 注册

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>注册</title>
    <style>
        div{
            width: 450px;
            height: 500px;
            border: 1px solid gray;
            padding: 10px;
        }
        span{
            border-bottom:2px solid purple;
            padding-bottom: 6px;
        }
        a{
            float: right;
            color: deepskyblue;
            text-decoration: none;
        }
        .inp1{
            width: 450px;
            height: 40px;
            border-radius: 5px;
            border: 1px solid green;
            margin-top: 20px;
        }
        .inp2{
            width: 320px;
            height: 40px;
            border-radius: 5px;
            border: 1px solid green;
            margin-top: 20px;
        }
        .yzm{
            width: 123px;
            height: 40px;
            border-radius: 5px;
            border: 1px solid pink;
            color: pink;
            background-color: white;
            margin-top: 20px;
        }
        .tu{
            width: 123px;
            height: 40px;
            border-radius: 5px;
            border: 1px solid pink;
            color: pink;
            background: url("https://tse1-mm.cn.bing.net/th/id/R-C.79a78eba70b41c99b3000d0cf5f5352d?rik=1LJg2oJDhVBc8Q&riu=http%3a%2f%2fwww.xiaobaixitong.com%2fd%2ffile%2fhelp%2f2018-08-06%2ff15ce5d652d8da38e9e0e384f35b39d7.png&ehk=9Piy2qOJgEjmFI%2f3BdqQyrGoTM%2b8OSxmfFfnFrzQnzg%3d&risl=&pid=ImgRaw&r=0") 0/123px 40px;
            vertical-align: middle;
        }
        .zhuc{
            width: 450px;
            height: 40px;
            border-radius: 5px;
            border: 1px solid green;
            background-color: deepskyblue;
            color: white;
            margin-top: 20px;
        }
    </style>
</head>
<body>
<div>
    <form>
        <span>请注册</span>
        <a href="2.html">立即登录 ></a>
        <hr>
        <input class="inp1" type="tel" placeholder="请输入手机号"/> <br />
        <input class="inp2" type="text" placeholder="请输入短信验证码"/>
        <input class="yzm" type="button" value="发送验证码"> <br />
        <input class="inp1" type="text" placeholder="请输入用户名"/> <br />
        <input class="inp1" type="password" placeholder="请输入密码"/> <br />
        <input class="inp1" type="password" placeholder="请再次输入密码"/> <br />
        <input class="inp2" type="text" placeholder="请输入图形验证码"/>
        <input class="tu" type="button"> <br />
        <input class="zhuc" type="submit" value="立即注册">
    </form>
</div>
</body>
</html>
```

### 登录

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>登录</title>
    <style>
        div{
            width: 450px;
            height: 300px;
            border: 1px solid gray;
            padding: 10px;
        }
        .span1{
            border-bottom:2px solid purple;
            padding-bottom: 6px;
        }
        a{
            float: right;
            color: deepskyblue;
            text-decoration: none;
        }
        .inp1{
            width: 450px;
            height: 40px;
            border-radius: 5px;
            border: 1px solid green;
            margin-top: 20px;
        }
        .dl{
            width: 450px;
            height: 40px;
            border-radius: 5px;
            border: 1px solid green;
            background-color: deepskyblue;
            color: white;
            margin-top: 20px;
        }
    </style>
</head>
<body>
<div>
    <form>
        <span class="span1">请登录</span>
        <a href="1.html">立即注册 ></a>
        <hr>
        <input class="inp1" type="tel" placeholder="请输入手机号"/> <br />
        <input class="inp1" type="password" placeholder="请输入密码" /> <br />
        <label><input type="checkbox" style="margin-top: 20px"/><span>七天内自动登录</span></label>
        <a href="?" style="color: grey;margin-top: 15px">忘记密码</a>
        <input class="dl" type="submit" value="登录">
    </form>
</div>
</body>
</html>
```



