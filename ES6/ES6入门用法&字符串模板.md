## 字符串模板
传统的JavaScript的输出模板是
```
$('#result').append(
  'There are <b>' + basket.count + '</b> ' +
  'items in your basket, ' +
  '<em>' + basket.onSale +
  '</em> are on sale!'
);
```
ES6引入了模板字符串来解决这个问题
```
$('#result').append(`
  There are <b>${basket.count}</b> items
   in your basket, <em>${basket.onSale}</em>
  are on sale!
`);
```
用反引号（`）来标识
```
// 普通字符串
`In JavaScript '\n' is a line-feed.`

// 多行字符串，会保留所有的空格和缩进
`In JavaScript this is
 not legal.`

console.log(`string text line 1
string text line 2`);

// 字符串中嵌入变量，需要将变量名写在${}之中
let name = "Bob", time = "today";
`Hello ${name}, how are you ${time}?`

//模板字符串之中还能调用函数。
function fn() {
  return "Hello World";
}

`foo ${fn()} bar`
// foo Hello World bar
```

