# 课件：CSS基础 

[TOC]

## CSS基本使用

```css
通过使用 CSS 我们可以大大提升网页开发的工作效率！
 CSS 同时控制多重网页的样式和布局。
 
 
样式表定义如何显示 HTML 元素，就像 HTML 中的字体标签和颜色属性所起的作用那样。样式通常保存在外部的 .css 文件中。我们只需要编辑一个简单的 CSS 文档就可以改变所有页面的布局和外观。
```

```css
什么是 CSS?
	CSS 指层叠样式表 (Cascading Style Sheets)
	样式定义如何显示 HTML 元素
	样式通常存储在样式表中
	把样式添加到 HTML 4.0 中，是为了解决内容与表现分离的问题
	外部样式表可以极大提高工作效率
	外部样式表通常存储在 CSS 文件中
	多个样式定义可层叠为一个
```

## CSS四种引入方式

```css
第一种：内联（在标签内直接写）
例如：
    <div style="height:500px;width:1000px;background-color: blanchedalmond;"></div>

这种方式会让html代码冗余，做小demo或者刚接触html的可以使用，但是不建议使用这种方式，知道有这种方式就可以了。
```

```css
第二种：内嵌(在head标签里，加一个style标签，在style里添加样式)
例如：
<head>
    <style>
        div{background-color:red;height: 300px;width: 300px;}
    </style>
</head>

<body>
<div></div>
</body>

这种方式会让这个页面太“重”了，同样是做小demo或者刚接触html的可以使用，也不建议使用。
```

```css
第三种：外联(新建一个.css文件，通过link来引入样式)
例如：

css:
	body{background-color: red;}

<body>
<link rel="stylesheet" href="xuyuan.css">
</body>

在css文件中，直接写样式即可，通过link来把样式引到.html文件中。这种方式是常用的方式，单独的一个css文件夹内放css的内容，把每个部分分的详细一些，也好去管理。
```

```css
第四种：导入（这种是在head标签里，加一个style标签，再写@import  url（），跟用link的方式差不多）
例如：
css:
	body{
    background-color: red;
    font-size: 12px;
    font-family: 宋体;
}



    <style>
        @import url(xuyuan.css);
    </style>
    
<body>
<h1>中文字，字体字体字体字体字体</h1>
</body>


跟link实现的效果一样，不同是link是页面加载的时候同时加载引入的样式，而@import是页面加载完成后，再加载引入的样式；并且link是xhtml中的标签，所以兼容所有浏览器，但@import是在CSS2.1提出的，所以低版本的浏览器会不兼容；link是可以通过js来改变样式的，@import就是不可以的；还有就是link可以引入除了css以为的其他文件，但@import只能引入css文件。
```

```css
CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明:

选择器		声明			声明
  h1 	{color:orange;text-align:center;}
选择器		属性 ：值			属性 ：值


选择器通常是您需要改变样式的 HTML 元素。
每条声明由一个属性和一个值组成。
属性（property）是您希望设置的样式属性（style attribute）。每个属性有一个值。属性和值被冒号分开。


CSS声明总是以分号(;)结束，声明总以大括号({})括起来:

为了让CSS可读性更强，你可以每行只描述一个属性:
p{color:red;text-align:center;}
```





## id、class、元素 选择器

```css
id选择器，是根据标签的id属性值选择对应的标签的。

<style>
#p1
{text-align:center;color:red;}
</style>

<body>
<p id="p1">Hello World!</p>
<p>这个段落不受该样式的影响。</p>
</body>

 ID属性不要以数字开头，数字开头的ID在 Mozilla/Firefox 浏览器中不起作用。
```

```css
元素选择器是根据标签的名称来选择对应的标签的。

<style>
div{color:red;font-size:10px;}
</style>

<body>
<div>Hello World!</div>
<p>这个段落不受该样式的影响。</p>
</body>

注意：id选择器优先级高于元素选择器
```

```css
class类选择器，是根据标签的class属性值选择对应的标签的。

<style>
.center{text-align:center;}
</style>

<body>
<h1 class="center">标题居中</h1>
<p class="center">段落居中。</p> 
</body>


你也可以指定特定的HTML元素使用class。
在以下实例中, 所有的 p 元素使用 class="center" 让该元素的文本居中，其他不管用:
<style>
p.center
{
	text-align:center;
}
</style>
<body>
<h1 class="center">这个标题不受影响</h1>
<p class="center">这个段落居中对齐。</p> 
</body>

 类名的第一个字符不能使用数字！
注意：类选择器选择器优先级高于元素选择器
```



## CSS选择器

```css
选择器的优先级：
Id选择器 > class 选择器 > 元素选择器
```

```css
群组化选择器:
常常我们的CSS 样式中会有好几个地方需要使用到相同的设定时，一个一个分开写会是一件满累人的工作，重覆性太高且显得冗长，更不好管理....在CSS 语法的基本设定中，就可以把这几个相同设定的选择器合并在一起，原本可能是写了7~8 行相同的语法，合在一起后就只要短短的一小行，怎么看都让人心旷神怡啊~

例如:
h1 { color:#666666; }
h2 { color:#666666; }
h3 { color:#666666; }
h4 { color#666666; }
ul { color:#666666; }
p { color:#666666; }
这些都是重复的设定

群组化：把这几个选择器使用逗号合并在一起，就只要短短的一小行，如下：
h1, h2, h3, h4, ul, p { color:#666666; } 

使用「群组化」选择器 可以使我们的CSS 样式变得比较简洁，将来又好管理和方便修改，这种写法是CSS 语法最基础的功能之一，只要把这一些基础的用法都熟悉了，同学们自然而然就可以练出漂亮的CSS 样式喽~
```

### css四个层次选择器：

```css
1.后代选择器
2.子代选择器
3.兄弟选择器
4.相邻选择器
```

```css
1.后代选择器
形如 div p(用一个空格隔开)选择的是指定标签下的所有对应的后代标签，儿子标签也属于后代标签的一个

<style>
		div p{
			color: red;
		}
</style>
<body>
	<div>
		<p>1</p>
		<p>2</p>
		<p>3</p>
		<ul>
			<li><p>4</p></li>
			<li><p>5</p></li>
			<li><p>6</p></li>
		</ul>
	</div>
</body>
```

```css
2.子代选择器
形如：div>p 选取的是指定id（或class或标签元素div等）下包含的指定子元素

<style>
	/* 选中的是div的子元素p，li下的p不属于div的子元素，li的p应属于ul的子元素*/
		div>p{
			color: red;
		}
	</style>
	<div>
		<p>1</p>
		<p>2</p>
		<p>3</p>
		<ul>
			<li><p>4</p></li>
			<li><p>5</p></li>
			<li><p>6</p></li>
		</ul>
	</div>

注意: 子元素也属于后代元素！当使用选择后代元素时div下的所有p都被选择，子元素只能是它的儿子


```

```css
3.兄弟选择器（之后所有兄弟选择器)
形如#name~p 即选择的是当前标签之后的所有同级标签

<style>
/*选择id为name的标签的之后所有同级p标签*/
		#name~p{
			background-color: red;
		}
</style>
<body>
	<p id="name">1</p>
	<p>2</p>
	<p>3</p>
</body>
```

```css
4.相邻选择器（下一个兄弟选择器）
形如#name+p 即选择的是当前标签的下一个同级标签(可进行多次叠加选择，但一般不使用多次叠加的方式选择)

<style>
/*选中id为name的下一个p标签*/
		#name+p{
			color: red;
		}
</style>
<body>
	<p id="name">1</p>
	<p>2</p>
	<p>3</p>
</body>
```

### 伪类选择器

```css
如果需要给超链接定义：访问前，鼠标悬停，当前被点击，已访问这4种伪类效果，而又没有按照一致的书写顺序，不同的浏览器可能会有不同的表现
超链接的4种状态，需要有特定的书写顺序才能生效。

超链接状态顺序：
a:link{}
a:visited{}
a:hover{}
a:active{}

```

```css
link实例，未访问过的样式：

<!DOCTYPE html>
<html lang="zh-cn">
<head>
<meta charset="utf-8" />
<title>CSS 链接伪类选择符 link选择器-CSS教程</title>
<style>
a:link{color:#03c;}
.external:link{color:#f00;}
</style>
</head>
<body>
<ul>
	<li><a href="?" class="external">外部链接</a></li>
	<li><a href="?">内部链接</a></li>
	<li><a href="?" class="external">外部链接</a></li>
	<li><a href="?">内部链接</a></li>
</ul>
</body>
</html>
```

```css
visited实例，访问过后的样式:

<!DOCTYPE html>
<html lang="zh-cn">
<head>
<meta charset="utf-8" />
<title>CSS 链接伪类选择符 visited选择器-CSS教程</title>
<style>
:link{color:#03c;}
:visited{color:#f00;}
</style>
</head>
<body>
<ul>
	<li><a href="http://www.baidu.com/" class="external">外部链接</a></li>
	<li><a href="http://www.bing.com/">内部链接</a></li>
	<li><a href="http://www.google.com/" class="external">外部链接</a></li>
	<li><a href="http://www.sougou.com/">内部链接</a></li>
</ul>
</body>
</html>
```

```css
hover实例,划过的样式：

<!DOCTYPE html>
<html lang="zh-cn">
<head>
<meta charset="utf-8" />
<title>CSS 用户行为伪类选择符 hover选择器-CSS教程</title>
<style>
h1{font-size:16px;}
a,div{display:block;margin-top:10px;padding:10px;border:1px solid #ddd;}
a:hover{display:block;background:#ddd;color:#f00;}
div:hover{background:#ddd;color:#f00;}
</style>
</head>
<body>
<h1>请将鼠标分别移动到下面2个元素上</h1>
<a href="?">我是一个a</a>
<div>我是一个div</div>
</body>
</html>
			
```

```css
active实例，激活的样式：

<!DOCTYPE html>
<html lang="zh-cn">
<head>
<meta charset="utf-8" />
<title>CSS 用户行为伪类选择符 active选择器-CSS教程</title>
<style>
h1{font-size:16px;}
a,div{display:block;margin-top:10px;padding:10px;border:1px solid #ddd;}
a:active{display:block;background:#ddd;color:#f00;}
div:active{background:#ddd;color:#f00;}
</style>
</head>
<body>
<h1>请将分别激活(点击与释放之间)下面2个元素</h1>
<a href="?">我是一个a</a>
<div>我是一个div</div>
</body>
</html>
```

```css
focus实例，设置对象在成为输入焦点（该对象的onfocus事件发生）时的样式。

<!DOCTYPE html>
<html lang="zh-cn">
<head>
<meta charset="utf-8" />
<title>CSS 用户行为伪类选择符 focus选择器-CSS教程</title>
<style>
h1{font-size:16px;}
ul{list-style:none;margin:0;padding:0;}
input:focus{background:#f6f6f6;color:#f60;border:1px solid #f60;outline:none;}
</style>
</head>
<body>
<h1>请聚焦到以下输入框</h1>
<form action="#">
	<ul>
		<li><input value="姓名" /></li>
		<li><input value="单位" /></li>
		<li><input value="年龄" /></li>
		<li><input value="职业" /></li>
	</ul>
</form>
</body>
</html>
```



## CSS字体/文本

### 字体常用样式

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
.h {
    font-family: "宋体";
	font-size: 16px;
	font-style: italic;
	font-weight: bold;
	font-variant: small-caps;

}
.hh {font: bold italic 16px italic 宋体 small-caps}
</style>
</head>


<body>
	<p>a测试字体</p>
	<p class="h">b测试字体</p>
	<p class="hh">c测试字体</p>
</body>
</html>
```

```css
1、字体 font-family
font-family: "字体","字体",
说明：如果在font-family属性中定义了多种字体，在浏览器中浏览时会由前向后选择字体，即当浏览器不支持“字体 1”时，则会采用“字体 2”；如果不支持“字体 1”和“字体 2”，即采用“字体 3”，以此类推。如果浏览器不支持font-family属性定义中的所有字体，则会采用系统默认的字体。

2、字号 font-size
在 HTML 中，字体的大小是由<font>标记中的size属性来控制的。在 CSS 里可以使用font-size属性来自由控制字体的大小。
语法：font-size: 大小的取值
font-size 的取值范围如下：
font-size: xx-small; /*绝对字体尺寸，最小*/
font-size: x-small; /*绝对字体尺寸，较小*/
font-size: small; /*绝对字体尺寸，小*/
font-size: medium; /*绝对字体尺寸，正常默认值*/
font-size: large; /*绝对字体尺寸，大*/
font-size: x-large; /*绝对字体尺寸，较大*/
font-size: xx0large; /*绝对字体尺寸，最大*/
font-size: larger; /*相对字体尺寸，相对于父对象中字体尺寸进行相对增大*/
font-size: smaller; /*相对字体尺寸， 相对于父对象中字体尺寸进行相对减小*/
font-size: 16px; /*绝对字体尺寸，使用像素值定义字体大小*/

3、字体风格 font-style
字体风格font-style属性用来设置字体是否为斜体。
语法：font-style: italic;
样式的取值有 3 种：normal是默认的正常字体；italic以斜体显示文字；oblique属于中间状态，以偏斜体显示。

4、加粗字体 font-weight
语法：font-weight: 字体粗细值
font-weight 的取值范围包括normal、bold、bolder、lighter、number。其中normal表示正常粗细；bold表示粗体；lighter表示特细体；number不是真正的取值，其范围是 100~900，一般情况下都是整百的数字，如 200、300 等。

5、小写字母转为大写 font-variant
使用font-variant属性可以将小写的英文字母转化为大写。
语法：font-variant: 取值
在 font-variant 属性种，可以设置的值只有两个，一个是 normal，表示正常显示，另一个是 small-caps，它能将小写的英文字母转化为大写字母且字体较小。

6、字体复合属性
可以设置 font 的符合属性，用来简化 CSS 代码。
语法：font: 字体的取值
复合属性可以取值字体族科、字体大小、字体风格、加粗字体等，各值之间用空格相连。
举例：.hh {font: bold italic 16px italic 宋体 small-caps}
```

### 文本常用样式

```css
对齐方式：
left		把文本排列到左边。默认值：由浏览器决定。
right		把文本排列到右边。
center		把文本排列到中间。
justify		实现两端对齐文本效果。
inherit		规定应该从父元素继承 text-align 属性的值。

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
h1 {text-align:center}
h2 {text-align:left}
h3 {text-align:right}
</style>
</head>
<body>
<h1>文本文档</h1>
<h2>文本文档</h2>
<h3>文本文档</h3>
</body>
</html>
```

```css
首行缩进
将段落的第一行缩进 50 像素：

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
p
  {
  text-indent:50px;
  }
</style>
</head>
<body>
<p>
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
这是段落中的一些文本。
</p>
</body>
</html>
```

```css
文本线:
none			默认。定义标准的文本。
underline		定义文本下的一条线。
overline		定义文本上的一条线。
line-through	定义穿过文本下的一条线。
blink			定义闪烁的文本。
inherit			规定应该从父元素继承 text-decoration 属性的值。


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
h1 {text-decoration: overline}
h2 {text-decoration: line-through}
h3 {text-decoration: underline}
h4 {text-decoration: blink}
</style>
</head>
<body>
<h1>这是标题 1</h1>
<h2>这是标题 2</h2>
<h3>这是标题 3</h3>
<h4>这是标题 4</h4>
</body>
</html>
```

![](.\web\属性失效.png)

```css
字距；增加或减少字符间的空白（字符间距）。



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
h1 {letter-spacing: -0.5em}
h4 {letter-spacing: 20px}
</style>
</head>
<body>
<h1>这是标题 1</h1>
<h2>这是标题 2</h2>
<h3>这是标题 3</h3>
<h4>这是标题 4</h4>
</body>
</html>
```

```css
词距，增加或减少单词间的空白（即字间隔）。

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
p.spread {word-spacing: 30px;}
p.tight {word-spacing: -0.5em;}
</style>
</head>
<body>
<p class="spread">I am Chinese</p>
<p class="tight">I am Chinese</p>
</body>
</html>

```

```css
行高
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
p.small {line-height: 90%}
p.big {line-height: 200%}
</style>
</head>
<body>
<p>
这是拥有标准行高的段落。
在大多数浏览器中默认行高大约是 110% 到 120%。
这是拥有标准行高的段落。
这是拥有标准行高的段落。
这是拥有标准行高的段落。
这是拥有标准行高的段落。
这是拥有标准行高的段落。
</p>

<p class="small">
这个段落拥有更小的行高。
这个段落拥有更小的行高。
这个段落拥有更小的行高。
这个段落拥有更小的行高。
这个段落拥有更小的行高。
这个段落拥有更小的行高。
这个段落拥有更小的行高。
</p>

<p class="big">
这个段落拥有更大的行高。
这个段落拥有更大的行高。
这个段落拥有更大的行高。
这个段落拥有更大的行高。
这个段落拥有更大的行高。
这个段落拥有更大的行高。
这个段落拥有更大的行高。
</p>
</body>
</html>
```

## CSS背景

```css
背景颜色：
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
body {background-color: yellow}
h1 {background-color: #00ff00}
h2 {background-color: transparent}
p {background-color: rgb(250,0,255)}
p.no2 {background-color: gray; padding: 20px;}
</style>
</head>
<body>
<h1>这是标题 1</h1>
<h2>这是标题 2</h2>
<p>这是段落</p>
<p class="no2">这个段落设置了内边距。</p>
</body>
</html>
```

```css
背景图片

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
body {background-image:url(图1.jpg);}
</style>
</head>
<body>

</body>
</html>
```

```css
背景铺盖
repeat			默认。背景图像将在垂直方向和水平方向重复。
repeat-x		背景图像将在水平方向重复。
repeat-y		背景图像将在垂直方向重复。
no-repeat		背景图像将仅显示一次。
inherit			规定应该从父元素继承 background-repeat 属性的设置。

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>

	body {background-image: url(图1.jpg);background-repeat: no-repeat}
</style>
</head>
<body>

</body>
</html>
```



```css
背景大小：
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>
body
{
background:url(图1.jpg);
background-size:63px 100px;
-moz-background-size:63px 100px; /* 老版本的 Firefox */
background-repeat:no-repeat;
padding-top:80px;
}
</style>
</head>
<body>
<p>上面是缩小的背景图片。</p>

<p>原始图片：<img src="图1.jpg" alt="Flowers"></p>
</body>
</html>
```



```css
背景定位，设置背景图像的起始位置。


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>

	body {
  background-image:url('图1.jpg');
  background-repeat:no-repeat;
  background-attachment:fixed;
  background-position:center;
}
</style>
</head>
<body>

</body>
</html>
```





```css
复合样式，把多个背景样式组合起来使用，简单易用。
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<style>

	body {
		background: blueviolet url("图1.jpg")  center no-repeat; width: 180px;height: 180px;
}
/*	body {
		background: blueviolet url("图1.jpg") repeat-x bottom center ; width: 180px;height: 180px;
}*/
</style>
</head>
<body>

</body>
</html>
```



​	