
# 如何实现table只刷新某一段数据
用一个变量来控制刷新是整个列表，还是刷新某一段数据

```
 canRefreshTableData: true //变量控制
```
核心代码如下：
```
getPrivateImages () {
	if (this.canRefreshTableData) {
    this.loading = true
  }
  Model.getList(.then(({data}) => {
    if (this.canRefreshTableData) {
      this.canRefreshTableData = false
      this.tableData = data
    } else {
      for (let i = 0; i < this.tableData.length; i++) {
        if (this.tableData[i].id === this.Id) {
          this.tableData[i].status = this.State
        }
      }
      this.$forceUpdate()
    }
    this.loading = false
  })
}
```
首先获取到数据渲染到页面时将canRefreshTableData设置为false
- 假如某个事件改变了某一字段的数据，要讲列表单项数据改变，就要找到相对应的数据，for循环出来if判断一下，然后将table里的数据更改即可。
- *注意：*当要重新获取列表数据时，要将变量置回true