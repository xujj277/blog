### 调用方式：
```
<vue-highcharts :options="options" :Highcharts="Highcharts" ref="xxxcharts"></vue-highcharts>
```
获得统计图
```
this.$refs.xxxcharts.getChart()
```
添加数据到统计图可以用addSeries的方式
```
chart.addSeries()
```
-------
若有多图的情况
- 可以将相同的options部分写进basicData中，统一调用
- 不同的数据部分可以通过下面方式单独提出
```
export let xxxdata = {
  name: 'xxx',
  data: [],
}
```
如果数据有变动还可以通过
```
xxxcharts.series[0].update({
    name: 'xxx',
    data: [],
})
```
update的方法是会把之前写的数据全部覆盖，相当于重新写
另外还有一种方法，是setdate但是只支持更新数据，不能更改相应的options
-----
## x轴24小时
若公司没有提供一个时间库的话，就只能自己来计算后端给的数据是多少份，然后在24个小时内平分。
x轴的格式有一定的要求。
```
  xAxis: {
    type: 'datetime',
    // tickAmount: 24,
    // tickInterval: 3600 * 1000,
    // minTickInterval: 3600 * 1000,
    dateTimeLabelFormats: {
      day: '%H:%M'
    }
```
```
const startTime = new Date(new Date() - 24 * 3600 * 1000)
const pointStart = Date.UTC(startTime.getFullYear(), 
startTime.getMonth(), startTime.getDate(), startTime.getHours(), startTime.getMinutes())
let pointInterval = 24 * 3600 * 1000 / this.chartData[0].data.length

lineChart.addSeries(Object.assign({}, item, {pointInterval}, {pointStart}))
```
------
### 没有数据时，展示提示
网上有的相关的官方的noData的提示，也引入相关的noData需要的东西，依旧没有显示那个“没有数据”的提示

只好最后，自己加了div来提示“没有数据”，只要自己v-if看是否有数据.length