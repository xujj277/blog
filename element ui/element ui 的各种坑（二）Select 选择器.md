#  element ui 的各种坑（二）Select 选择器
- 这里的各种坑，并不代表element ui 不好，只是记录自己没有仔细看文档例子，而踩的坑。
---
select选择器中提供了value值，el-option会将value值传递给el-select中的v-model

Value值一般就是之后要传递给后端的一段数据，但总有时候后端不仅仅要的是一段数据，可能需要的是两个字段，这时候我就会想把value值写成一个对象。如下：
```
<el-select v-model="internet" placeholder="请选择所属网络">
  <el-option v-for="(item, key) in tableData" :key="key" :label="item.name" :value="{id: item.id, name: item.name}">
	</el-option>
</el-select>
```

但会出现问题，v-model*只传递了最后一个对象的value值，*并且里面option都是被选择的状态，这显然不符合需求
![](https://i.loli.net/2018/11/20/5bf418bfd618e.png)

- 经过查找，需要一个这样的字段放在el-select上
```
value-key="id"
```
这个字段所输入的值，值为数据源数组元素中的唯一键，比如此例子中的id或者name
