#1. post 和 get 方式提交数据有什么区别？
- GET - 从指定的资源请求数据。会在URL上显示参数，不安全。传输的参数有长度限制。
- POST - 向指定的资源提交要被处理的数据。不会URL上显示参数。传输的参数没有长度限制。
#2. 在input里，name 有什么作用？
name 属性用于对提交到服务器后的表单数据进行标识，或者在客户端通过 JavaScript 引用表单数据。
#3. radio如何分组
表单中的单选框radio，name相同的是一组，比如以下代码：
```
<form>
    <input type="radio" name="sex" value="male"> 男 <br>
    <input type="radio" name="sex" value="female"> 女<br>
    <input type="radio" name="age" value="adult"> 已成年<br>
    <input type="radio" name="age" value="child"> 未成年
  </form>
```
![radio，name相同的是一组](https://upload-images.jianshu.io/upload_images/10142252-a871c2df47c3c1cb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#4.placeholder 属性有什么作用？
- 提供可描述输入字段预期值的提示信息，该提示会在输入字段为空时显示，并会在字段获得焦点时消失。
- 也就是说能够让你在文本框里显示提示信息，一旦你在文本框里输入了什么信息，提示信息就会隐藏。

#5. CSRF 攻击是什么？如何防范？
 一、跨站请求伪造。攻击者盗用了你的身份，以你的名义发送恶意请求。CRSF能做的事情包括利用你的身份发邮件，发短信，进行交易转账，甚至盗取账号信息。
二、
1. 验证 HTTP Referer 字段
HTTP头中的Referer字段记录了该 HTTP 请求的来源地址。在通常情况下，访问一个安全受限页面的请求来自于同一个网站，而如果黑客要对其实施 CSRF攻击，他一般只能在他自己的网站构造请求。因此，可以通过验证Referer值来防御CSRF 攻击。
2. 验证码。
通常情况下，验证码能够很好的遏制CSRF攻击。
3. token
可以在 HTTP 请求中以参数的形式加入一个随机产生的 token，并在服务器端建立一个拦截器来验证这个 token，如果请求中没有token或者 token 内容不正确，则认为可能是 CSRF 攻击而拒绝该请求。
在POST 上，要在 form 的最后加上 <input type="hidden" name="csrftoken" value="tokenvalue"/>，这样就把token以参数的形式加入请求了。

#6. type=hidden隐藏域有什么作用? 举例说明
隐藏域是用来收集或发送信息的不可见元素，对于网页的访问者来说，隐藏域是看不见的。当表单被提交时，隐藏域就会将信息用你设置时定义的名称和值发送到服务器上。

1. 后端接收前端传来的数据，需要确认前端的身份，是本公司的网页传来的数据，而不是其他黑客知道后端地址后传来的假数据。那么就加一个隐藏域，验证value里的值和数据库里name的值是不是对应的。

2. 有时候一个表单里有多个提交按钮，后端怎么知道用户是点击哪个按钮提交过来的呢？这时候我们只要加隐藏域，对每一个按钮起个名字(value值)，后端接收到数据后，检查value值，就能知道是哪个按钮提交的了。

3. 有时候一个网页中有多个form，我们知道多个form是不能同时提交的，但有时这些form确实相互作用，我们就可以在form中添加隐藏域来使它们联系起来。

#7. label 有什么作用？如何使用？
<label> 标签为 input 元素定义标注（标记）。

label 元素不会向用户呈现任何特殊效果。不过，它为鼠标用户改进了可用性。如果您在 label 元素内点击文本，就会触发此控件。就是说，当用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上。

Label标识有两个属性，一个是for，一个是 accesskey。

for属性：
功能：表示这个Lable是为哪个控件服务的，Label标签要绑定了FOR指定HTML元素的ID或name属性，你点击这个标签的时候，所绑定的元素将获取焦点。
用法：<label for="InputBox">姓名</label><input id="InputBox" type="text">
accesskey属性：
功能：定义了访问这个控件的热键。
用法：<label for="InputBox" accesskey＝"N">姓名</label><input id="InputBox" type="text">
局限性：accessKey属性所设置的快捷键不能与浏览器的快捷键冲突，否则将优先激活浏览器的快捷键。

#8. 以下input有何作用？
```
<input type="submit" value="提交">  
```
具有提交表单的功能
