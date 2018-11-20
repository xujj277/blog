# element ui 的各种坑（三）Form表单&&prop和rules
- 这里的各种坑，并不代表element ui 不好，只是记录自己没有仔细看文档例子，而踩的坑。
---
首先，prop和rules是用于form表单验证的，他有两种方式的写法

1. 第一种最常见，将rules写在el-form上
```
<el-form ref="loginForm" :model="loginInfo" :rules="loginRules">
   <el-form-item prop="username">
      <el-input v-model="loginInfo.username"></el-input>
  	 </el-form-item>
   <el-form-item prop="password">
      <el-input type="password" v-model="loginInfo.password" @keyup.enter.native="login('loginForm')"></el-input>
   </el-form-item>
</el-form>
```
Data里面就要这么写：
```
loginRules: {
        username: [{ required: true, message: '请输入您的登录邮箱', trigger: 'blur' }],
        password: [{ required: true, message: '请输入您的密码', trigger: 'blur' }]
}
```
- *注意事项：*
![](https://i.loli.net/2018/11/20/5bf41b6a53060.png)
这些字段必须是相同的！！！不相同的话，表单会无法验证！！！（真滴坑……）

2. 将rules写在el-form-item上
```
<el-form ref="loginForm" :model="loginInfo">
  <el-form-item prop="username" :rules="{ required: true, message: '请输入您的登录邮箱', trigger: 'blur' }">
   <el-input v-model="loginInfo.username"></el-input>
  </el-form-item>
</el-form>
```
当el-form里的东西是v-for循环出来的时候，这个方法具有奇效。