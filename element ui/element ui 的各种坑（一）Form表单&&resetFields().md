# element ui 的各种坑（一）Form表单&&resetFields()
- 这里的各种坑，并不代表element ui 不好，只是记录自己没有仔细看文档例子，而踩的坑。
---
- 每次做各种form表单时，首先要注意的是初始化，但是刚开始若没有仔细看文档，则会自己写个方法将数据设置为空，如：
```
data () {
	return {
		data：[]
	}
methods: {
	resetForm () {
			this.data = []
		}
	}
}
```
但是这样就会出现一个问题，表单内存在各种验证，假如是一个弹框内有form表单，弹框出现就执行上述代码，可能会出现表单验证的错误提示仍然保留的情况。
- 细看文档，提供了一个resetFields()的方法
```
this.$refs[formName].resetFields()
```
不仅可以帮你初始化数据，还可以将验证提示消除！！！
---
*注意：* 
1. 由于ref存在，若是在弹框里面，要在弹框出现后才执行resetFields()
所以得如下操作： 
```
this.$nextTick(() => {
	this.$refs[formName][0].resetFields()
})
```
2. 另外调用 resetFields 方法需要 form-item 组件中配置 prop 属性。
