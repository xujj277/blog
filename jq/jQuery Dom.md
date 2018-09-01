
# 一、以下 jQuery 方法有什么作用？如何使用？给出范例
.append()
.prepend()
.before()
.after()
.remove()
.empty()
.html()
.text()

[demo](http://js.jirengu.com/ritopigake/1/edit?html,js,output "null")
# 二、```$node.text()```和```$node.html()```有什么区别？

```$node.text()```只是会将里面的内容都显示出来。
```$node.html()```若里面有标签则会将其先经行解析之后再显示出来。但有可能会引入xss攻击，若有人页面放入一个script，容易形成漏洞。而text就不会这种问题，可创建一个节点，若是恶数据，只会展示而不会运行。
```
$('.container1').html('<h1>我是标题</h1>')
$('.container2').text('<h1>我不是是标题</h1>')
```
![区别](https://upload-images.jianshu.io/upload_images/10142252-5d2e955c38fd1567.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
# 三、介绍以下 jQuery 函数的用法，给出范例
.val()
.attr()
.removeAttr()
.prop()
.css()
.addClass()
.removeClass()
.hasClass()
.toggleClass()

  [demo](http://js.jirengu.com/qanefezaga/1/edit?html,js,output "null")
# 四、jQuery 对象和原生 Dom 对象有什么区别？如何相互转换？
是两种不同的对象类型，并且两者的方法不能混用。
jQuery是类数组对象，并不是数组
- this是原生Dom对象，若要用到this则要加入$(this)
- 当判断一个对象存不存在时，会有区别：
    - jQuery仍然会显示出一个对象，可以通过.length是不是0来判断是否存在这个对象。
    - 而原生DOM对象会输出null，来表示不存在。
## 相互转换
- jQuery对象转换成原生Dom对象：可以在```$()```的后面加入[index]中括号加数字，来获得其中的相应的原生DOM对象，如
```$('#p1')[0]```
- 原生Dom对象转换成jQuery对象：可以在原生DOM对象的外面加```$()```来获得相应的jQuery对象，如
```$(document.querySelector('#p1'))```
# 五、介绍以下 jQuery 方法的用法，给出范例
.each()
$.extend()
.clone()
.index()
.ready()
```
$(document).ready(function(){
    //放在开头时，所要执行的代码会等到元素加载完之后才执行。
})
```
[demo](http://js.jirengu.com/copihunumi/1/edit?js,console,output "null")
# 六、window.onload和$(document).ready有什么区别？document.onDOMContentLoaded呢?
### 执行时间不同
- 当```window.onload```事件触发时，页面上所有的DOM，样式表，脚本，图片，flash都已经加载完成了。
- ```$(document).ready()```时DOM结构绘制完毕后就执行，不必等到加载完毕。
- ```document.onDOMContentLoaded```等html文档被完全加载和解析时触发，而不等待样式表和图像等的加载。

### 编写个数不同
- ```window.onload```不能同时编写多个，如果有多个则只能执行一个。
- ```$(document).ready()```可以执行多个
# 七、实现如下效果，点击 icon 后会切换播放和暂停两种状态
[demo](http://js.jirengu.com/vaboyumopo/1/edit?html,css,js,output "null")





