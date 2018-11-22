# element ui table 中的selection实现单选
- 首先去除左上角的那一个全选按钮
![](https://i.loli.net/2018/11/22/5bf619d4dc2f1.png)

这里用的方法是css ，让他display: none：
```
thead {
    .el-table-column--selection {
      .cell {
        display: none;
      }
    }
  }
```
- 然后要用到@selection-change这个属性来当选择项发生变化时会触发该事件
这里思想就是当多选的时候，就去除全部选择，然后勾选上最后一个选项。
如下：
```
chooseInstance (val) {
      if (val.length > 1) {
        this.$refs.Table.clearSelection()
        this.$refs.Table.toggleRowSelection(val.pop())
      } else {
		}
    },
```

- 如果要实现点击table一列的任意位置就勾选上，要用到@current-change这个属性来当点击表格当前行触发事件，可用如下方式： 
```
this.$refs.Table.toggleRowSelection(val)
```
