
## 一、任意类型转字符串
### 1. xxx.toString()
![image](http://upload-images.jianshu.io/upload_images/10142252-6cd4daeb5b76f439.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
其中null、undefined不能用，object不能转换成相对应的。

### 2. x + ''
这个最为常用
都能转换

### 3. String() 功能和2一样强大

---
## 二、任意类型转布尔

### 1. xxx.Boolean()
### 2. !!x   （墙裂推荐，比较好装逼）

- 所有数据类型中只有5个例外是falsy值，对象是没有falsy值的（空数组也是true）的
number： 0   和   NaN
string:  ''
null
undefined
  
## 三、如何转换成number？
### '1' -> 1 
1. Number('1') 
2. parseInt('1', 10)
3. parseFloat('1.23')
4. '1'- 0    (最常用)
5. +'1'

## 四、内存
stack 栈内存（number、string、undefined、symbol、boolean，简单）
Heap 堆内存（对象在这，地址，复杂）

1. 
```
var a = {name: a}
b = a
b = {name: b}
a.name = ?
```

![image](http://upload-images.jianshu.io/upload_images/10142252-b1bb3e18a0e6fad1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
a

2. 
```
var a = {name: a}
b = a
b.name = b
a.name = ?
```
 b

3. 
```
var a = {name: a}
b = a
b = null
a = ?
```
{name: a}

引用类型易错题
![image](http://upload-images.jianshu.io/upload_images/10142252-6622d2f5e57ffe66.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
---

# 垃圾回收
如果一个对象没有被引用，它就是垃圾，将被回收

```
var fn = function () {}
document.body.onclick = fn
fn = null
```
问```function(){}```是不是垃圾？
![image](http://upload-images.jianshu.io/upload_images/10142252-a100e02cd8c62fb9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)不是

若把页面关了，则fn变成垃圾，heap里面的东西也是垃圾。但IE6认为heap里面不是垃圾，所以这是IE6的bug，用如下方式解决：
```
window.onunload = funtion () {
	document.body.onclick = null
}
```
在页面关闭之前，把所有事件都置为null

---

# 浅拷贝 vs 深拷贝
基本类型的赋值都是深拷贝。
现在只讨论复杂类型即对象的情况：

**深拷贝：我被赋值之后，你不变**
**浅拷贝：我被赋值之后，你也变**

