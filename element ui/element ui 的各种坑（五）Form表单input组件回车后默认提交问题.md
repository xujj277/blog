# element ui 的各种坑（五）Form表单input组件回车后默认提交问题
回车提交事件可以用如下方式： 
```
@keyup.enter.native="handleChange"
```

但是写项目时发现，有的input组件会有个默认回车提交的情况。一点回车就会刷新整个页面，但是并没有发生什么改变。

所以这是个bug，可以用如下方式解决，加多一条@submit.native.prevent在el-form-item 上：
```
<el-form-item label="xxx" @submit.native.prevent>
     <el-input v-model="name"></el-input>
</el-form-item>
```
