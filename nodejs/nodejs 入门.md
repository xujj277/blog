## 引入
```
var fs = require('fs')
```
```require ```的方式来引入组件和自己写的文件
```
var strApi = require('./stringApi')
```
stringApi.js中要用到```exports```方式才可以被引入
```
function replaceDigit(str) {
  return str.replace(/\d/gm, '')
}
module.exports.replaceDigit = replaceDigit
```

## node中有很多api
```
fs.readFile('file.txt', 'utf8', function (err, str) {
  if(err) {
    console.log('error...');  
  }else {
    var strAfter = strApi.replaceDigit(str)
    console.log(strAfter)

    fs.writeFile('fileAfter.txt', strAfter, function (err) {
      if(err) throw err;
      console.log('asdfjag')
    })
  }
})
```
比如```readFile writeFile```等


