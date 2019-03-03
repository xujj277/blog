- 目标数据结构：
```js
options: [{
          value: 'zhinan',
          label: '指南',
          children: [{
            value: 'shejiyuanze',
            label: '设计原则',
            children: [{
              value: 'yizhi',
              label: '一致'
            }, {
              value: 'fankui',
              label: '反馈'
            }, {
              value: 'xiaolv',
              label: '效率'
            }, {
              value: 'kekong',
              label: '可控'
            }]
          }]
    }]
```
- 原始数据结构（省市级数据结构简化）：
```
const data = [
  {
  value: 1, parent: 0
}, {
  value: 2, parent: 0
}, {
  value: 3, parent: 1
}, {
  value: 4, parent: 1
}, {
  value: 5, parent: 2
}, {
  value: 6, parent: 2
}, {
  value: 7, parent: 3
}, {
  value: 8, parent: 7
}]
```
>为了更方便查找到每个数据对应的```value```和```parent```值，在对象中取值比在数组中取值更加方便，只需要 ```xxx.value```或者```xxx[value]```方式即可。

所以需要将```data```这个数组转成一个```map```的哈希表
```
const map = {}
const result = []
data.forEach(i => {
  map[i.value] = i
  if (i.parent === 0) result.push(i)  // 先找到省这一列的数据
})
```
> 然后就是将对应的市放到对应的省份下面的```children```里，区放到对应的市里

这里运用了一个对象的存值的属性。先要看```map```里面的所有对象里是否有```parent```，有```parent```的就将里面的```children```做一个初始化，然后将对应的那一条数据```i```存进去。

由于```result```里面的对象和```map```里面的对象是指向同一个地址里面的，所以当```map```增加```children```这个属性的时候，```result```也会增加。

```
data.forEach(i => {
  const parent = map[i.parent]
  if (parent) {
    if (!parent.children) {
      parent.children = []
    }
    parent.children.push(i)
  }
})
this.options = result
```


