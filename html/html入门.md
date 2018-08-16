# 1. 常见的浏览器有哪些，内核是什么？
可以分这四种：Trident，Gecko，Webkit，Chromium/Bink，Presto。看着都很陌生，那么换个样子：IE，Mozilla FireFox，Safari，Chrome、Opera

#2. doctype有什么作用？怎么写？
它是指示 web 浏览器关于页面使用哪个 HTML 版本进行编写的指令，浏览器才能获知文档类型。
  - 确切说doctype告诉浏览器解释器怎么解释文档
```<!DOCTYPE html>```

#3. 页面出现了乱码，是怎么回事？如何解决？
- 主要是html源代码内中文字内容与html编码不同造成
html网页编码是gbk，而程序从数据库中调出呈现是utf-8编码的内容也会造成编码乱码

- 在head里设置好<meta charset="UTF-8">格式

#4. meta 有哪些常见的值？
1.```<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">```
控制页面在移动端不缩小显示
2.```<meta name="description" content="">```
这里是网页的描述，是给搜索引擎看的，搜索引擎根据这个描述进行收录排名，一般是网页内的关键字。
3.```<meta name="keywords" content="">```
keywords用来告诉搜索引擎你网页的关键字是什么，换句话说就是你的网站主题，从一定意义上来说keywords与description其实它们的作用是一样的（突出网站主题），但他们又有所不同（在搜索结果页的展示）。
4.```<meta http-equiv="Refresh" content="2;URL">```
自动刷新并转到新页面。其中的2是指停留2秒钟后自动刷新到URL网址。
5.```<meta http-equiv="content-Type" content="text/html; charset=utf-8">```
设定页面使用的字符集。在HTML5中已经简写成```<meta charset="utf-8">```
6.```<meta http-equiv="Expires" Content=0>```
可以用于设定网页的到期时间。一旦网页过期，必须到服务器上重新传输。

#5.如何在html 页面上展示 <div></div> 这几个字符？
&lt;div&gt;&lt;/div&gt;

#6.title 属性和 alt属性分别有什么作用？
- alt属性
是为了给那些不能看到你文档中图像的浏览者提供文字说明。这包括那些使用本来就不支持图像显示或者图像显示被关闭的浏览器的用户，视觉障碍的用户和使用屏幕阅读器的用户。替换文字是用来替代图像而不是提供额外说明文字的。alt属性包括替换说明，对于图像和图像热点是必须的。它只能用在img、area和input元素中

- title属性
为设置该属性的元素提供建议性的信息。使用title属性提供非本质的额外信息。大部分的可视化浏览器在鼠标悬浮在特定元素上时显示title文字为提示信息，然而这又由制造商来决定如何渲染title文字。
title属性有一个很好的用途，即为链接添加描述性文字，特别是当连接本身并不是十分清楚的表达了链接的目的。这样就使得访问者知道那些链接将会带他们到什么地方，他们就不会加载一个可能完全不感兴趣的页面。另外一个潜在的应用就是为图像提供额外的说明信息，比如日期或者其他非本质的信息。
title属性可以用在除了base，basefont，head，html，meta，param，script和title之外的所有标签。但是并不是必须的。