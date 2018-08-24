# let
```let```声明的变量只在它所在的代码块中有效。
```
{
  let a = 10;
  var b = 1;
}

a // ReferenceError: a is not defined.
b // 1
```
```
for (let i = 0; i < 10; i++) {
  // ...
}

console.log(i);
// ReferenceError: i is not defined
```
如果把```let```换成```var```，则会出现下面情况：
```
var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 10
```
因为```i```是由```var```所声明的，全局里面只有一个```i```，所以每次i发生改变就内部的```console.log(i)```也会发生改变

如果改用let的，则不会出现上面情况
```
var a = [];
for (let i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 6
```
```i```是由```let```声明的所以只会在本轮循环中有效。**你可能会问，如果每一轮循环的变量i都是重新声明的，那它怎么知道上一轮循环的值，从而计算出本轮循环的值？这是因为 JavaScript 引擎内部会记住上一轮循环的值，初始化本轮的变量i时，就在上一轮循环的基础上进行计算。**

### 暂时性死区
ES6 明确规定，如果区块中存在```let```和```const```命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些变量，就会报错。

总之，在代码块内，使用```let```命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 TDZ）。
```
if (true) {
  // TDZ开始
  tmp = 'abc'; // ReferenceError
  console.log(tmp); // ReferenceError

  let tmp; // TDZ结束
  console.log(tmp); // undefined

  tmp = 123;
  console.log(tmp); // 123
}
```
总之，暂时性死区的本质就是，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。
### 不允许重复声明
```let```不允许在相同作用域内，重复声明同一个变量。
```
// 报错
function func() {
  let a = 10;
  var a = 1;
}

// 报错
function func() {
  let a = 10;
  let a = 1;
}
```
因此，不能在函数内部重新声明参数。
```
function func(arg) {
  let arg; // 报错
}

function func(arg) {
  {
    let arg; // 不报错
  }
}
```
# const
```const```声明一个只读的常量。一旦声明，常量的值就不能改变。
```
const PI = 3.1415;
PI // 3.1415

PI = 3;
// TypeError: Assignment to constant variable.
```
上面代码表明改变常量的值会报错。
```const```声明的变量不得改变值，这意味着，```const```一旦声明变量，就必须立即初始化，不能留到以后赋值。

#总结
**let：**
1. 作用域只在最近的```{}```之间
2. 若```let a```之前使用```a```，就会报错
3. 若重复```let a ```，那么报错

**const：**
1.2.3 同上
4.只有一次赋值的机会，并且必须在声明的时候立马赋值
