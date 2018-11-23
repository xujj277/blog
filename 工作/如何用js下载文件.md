# 如何用js下载文件
```
var a = document.createElement('a')
var url = window.URL.createObjectURL(new Blob([data]))
var filename = downloadOptions.fileName
a.href = url
a.download = filename
a.target = '_blank'
a.click()
```