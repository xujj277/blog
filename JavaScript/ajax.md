# 一、ajax 是什么？有什么作用？

- ajax并不是一项新技术，它是2005年由jesse james garrett创造的一个术语，它描述了一种“新”方法，将多种现有技术结合在一起使用，包括html或xhtml，级联样式表，JavaScript，文档对象模型，xml，xslt，最重要的是xmlhttprequest对象。
当这些技术结合在ajax模型中时，Web应用程序能够快速，增量更新用户界面，而无需重新加载整个浏览器页面。
- 这使应用程序更快，更响应用户操作。
尽管ajax中的x代表xml，但json现在使用的不止是xml，因为它具有许多优点，如轻量级和JavaScript的一部分。
json和xml都用于在ajax模型中打包信息。

- 而其中最核心的依赖是浏览器提供的XMLHttpRequest对象，是这个对象使得浏览器可以发出HTTP请求与接收HTTP响应。 实现在页面不刷新的情况下和服务端进行数据交互。

- ajax是一组使用客户端上的许多Web技术创建异步Web应用程序的Web开发技术。
通过ajax，Web应用程序可以异步（在后台）发送和检索服务器中的数据，而不会干扰现有页面的显示和行为。
通过将数据交换层与表示层分离，ajax允许网页和扩展Web应用程序动态更改内容，而无需重新加载整个页面。
在实践中，由于json本身是javascript的优势，所以现代实现通常使用json而不是xml。html和css可以结合使用来标记和样式信息。
然后可以通过javascript修改网页以动态显示 - 并允许用户与新信息交互。
JavaScript内置的xmlhttprequest对象通常用于在网页上执行ajax，从而允许网站在不刷新页面的情况下将内容加载到屏幕上。
ajax也不是一项新技术或另一种不同的语言，只是以新方式使用现有技术。
# 二、如何 mock 数据？
### server-mock
使用 server-mock node工具启动一个能处理静态文件和动态路由的服务器

### 用githubpages mock数据

- 在git里面创建相应的html和json文件
html内写
```
<!doctype html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
<script>
  var xhr = new XMLHttpRequest()
  xhr.open('GET','/mock/cate.json',true)
  xhr.send()
  xhr.onload = function(){
    console.log(JSON.parse(xhr.responseText))
  }
</script>
</body>
</html>
```
在json文件里面写入json格式的内容就可以mock到该数据了

### 在线上mock数据
例如用Easy mock的网站来mock数据，可以在网站上得到一个URL
# 三、把GET 和 POST 类型的 ajax 的用法手写一遍，如
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script>
		var xhr = new XMLHttpRequest()
		xhr.open('Get','/login?username=jirengu&password=123',true)
		xhr.send()

		xhr.onreadystatechange = function(){
			if(xhr.readyState === 4 && xhr.status === 200){
				console.log(xhr.responseText)
			}
		}
		//GET的使用
//status 是服务器是否正常
//readystate是交互流程是否结束
//load是readystate是4了

		xhr.addEventListener('readystatechange',function(){
			console.log('readystate:',xhr.readystate)
		})
		xhr.addEventListener('load',function()}{
			console.log(xhr.status)
			if(xhr.status >= 200  && xhr.status < 300 || xhr.status === 304){
				var data = xhr.responseText
				console.log(data)
			}else{
				console.log('error')
			}
		})
		xhr.onerror = function(){
			console.log('error')
		}

//POST 过程

		var xhr = new XMLHttpRequest()
		xhr.open('POST','/login',true)
		xhr.send('username=jirengu&password=123')

		xhr.addEventListener('load',function()}{
			console.log(xhr.status)
			if(xhr.status >= 200  && xhr.status < 300 || xhr.status === 304){
				var data = xhr.responseText
				console.log(data)
			}else{
				console.log('error')
			}
		})
		xhr.onerror = function(){
			console.log('error')
		}
	</script>
</body>
</html>
```
# 四、封装一个 ajax 函数，能实现如下方法调用
```
function ajax(options){
    //补全
}
ajax({
    url: 'http://api.jirengu.com/weather.php',
    data: {
        city: '北京'
    },
    onsuccess: function(ret){
        console.log(ret)
    },
    onerror: function(){
        console.log('服务器异常')
    }
})
```
```
//封装一个ajax
function ajax(opts){
	var url = opts.url
	var type = opts.type || 'GET'
	var dataType = opts.dataType || 'json'
	var onsuccess = opts.onsuccess || function(){}
	var onerror = opts.onerror || function(){}
	var data = opts.data || {}

	var dataStr = []
	for(var key in data){
		dataStr.push(key + '=' + data[key])
	}
	dataStr = dataStr.join('&')

	if(type === 'GET'){
		url += '?' + dataStr
	}

	var xhr = new XMLHttpRequest()
	xhr.open(type,url,true)
	xhr.onload = function(){
		if((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){
			//成功了
			if(dataType === 'json'){
				onsuccess(JSON.parse(xhr.responseText))
			}else{
				onsuccess(xhr.responseText)
			}

	} else{
		xhr.send()
		}
	}
   ```
