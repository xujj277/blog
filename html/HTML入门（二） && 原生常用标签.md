
---
## 1. form
> 跳转页面（HTTP POST请求）
- 如果form表单中没有提交按钮就无法提交
```
<input type=“submit” value=“提交”>
```

### 提交内容被查看（method属性）
- post 请求会在chrome开发者工具的Network中的Form Data中看到自己提交的内容（明文会被查看）
- get 请求会在url的参数上带上自己提交的内容（明文会被查看）

### target 属性
- ```_self```在当前HTML4或HTML5文档页面重新加载返回值。这个是默认值。译注：也就是说如果这个文档在一个frame中的话，self是在当前frame（document）中重新加载的，而不是整个页面。**(自身)**
- ```_blank```: 新窗口。
- ```_parent```: 在父级的frame中以HTML4或HTML5文档形式加载返回值，如果没有父级的frame，行为和_self一致
- ```_top```: 如果是HTML 4文档: 清空当前文档，加载返回内容；HTML5: 在当前文档的**最高级**内加载返回值，如果没有父级，和_self的行为一致
---
## 2. input
### input和button的区别： 
> - button如果没有写type属性，就自动升级成一个提交按钮。而写了```type=“button”```，就会没有反应。
> - input 中如果```type=“button”```只是一个普通按钮，点击没有反应。而设置为submit就会是一个提交按钮。
> - input是没有子元素的，button是可以有子元素的。

### type 属性
- checkbox （name 相同的为一组，多选框）
- text
- radio（name 相同的为一组，单选框）
- password

*小贴士：*
1. 用label把input标签包起来可以使得点击前面的字段触发input输入
```
<label>用户名<input type=“text” name=“xxx”></label>
```
2. form 标签里面的 input 加不加 name 属性由什么区别？
> 如果 input 不加 name，那么在表单提交时，input 的值就不会出现在请求里
---
## 3. select
```
  <select name="group" multiple>
    <option value="">-</option>
    <option value="1" disabled>第一组</option>
    <option value="2" selected>第二组</option>
  </select>
```
## 4. textarea
- cols （列，一般不准）
- rows （行，准的）
- 一定要给name

## 5. table
![image](http://upload-images.jianshu.io/upload_images/10142252-c9e5e8f7d55ff4d2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 6. a
> 跳转页面（HTTP GET请求）
### target属性
和form里面的一致

### download属性
- 下载

### href 属性
- 如果直接写```qq.com```，会不会跳转？
> 不会！这是一个相对地址，打开的其实是一个文件。.com其实被当做文件后缀。
1. 加上http/https，即可。
2.  或者//qq.com，即表示当前协议是什么协议就是什么协议。

- 如果直接写```?name=xxx```呢？
> 浏览器会自动把这段加到最后面当做参数，发送了一个GET请求

- ```# ```锚点是不发请求的，直接到达顶部，其他都是要发请求的（还除了伪协议）

#### 伪协议 javascript: ;  
满足a标签点击了什么都不做的需求
