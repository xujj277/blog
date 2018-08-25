#一、jquery 如何绑定事件？直接绑定和使用事件代理分别如何使用
### .on( events [,selector ] [,data ], handler(eventObject) )直接绑定和使用事件代理绑定
1. events：一个或多个空格分隔的事件类型和可选的命名空间，或仅仅是命名空间，比如"click"。
2. selector：一个选择器字符串，用于过滤出被选中的元素中能触发事件的后代元素。如果选择器是 null 或者忽略了该选择器，那么被选中的元素总是能触发事件
3. data：当一个事件被触发时，要传递给事件处理函数的event.data
4. handler(eventObject)：事件被触发时，执行的函数。若该函数只是要执行return false的话，那么该参数位置可以直接简写成 false

### 直接绑定和使用事件代理分别如何使用

[demo](http://js.jirengu.com/yigasobibo/1/edit?html,js,console,output "null")

#二、jQuery 如下函数如何使用？演示使用方式
  [demo](http://js.jirengu.com/cumorahezu/1/edit?html,js,output)
#三、介绍一些函数的用法，给出范例
```$.ajax```
```$.get```
```$.getJSON```
###$.ajax
```
$.ajax ({
  url: 'http://xxx',//请求的一个接口
  type: 'GET',
  data: {
    username: 'xujinjun',
    password:　'xu123456'
  },
  dataType:　'json'//请求从服务器加载JSON编码的数据
}).done(function(){
  //数据请求成功后执行的操作
}).fail(function(){
  //数据请求失败后执行的操作
}).always(function(){
  //无论成功与否所执行的操作
})
```
这样就发送了一个GET请求
还有一个更简单的发送GET请求的方式就是$.get
###$.get
   ```
$.get('http://api.jirengu.com/weather.php').done(function(ret){
console.log(ret)
})
```
###$.getJSON
```
$.getJSON('http://api.jirengu.com/weather.php',function(ret){
console.log(ret)
})
```

