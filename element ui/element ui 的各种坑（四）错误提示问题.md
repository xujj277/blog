# element ui 的各种坑（四）错误提示问题
```
<el-form-item label="密码:" prop="password" v-if="resetSystemForm.loginSet === 'password'">
   <el-input type="password" v-model="resetSystemForm.password" placeholder="请输入密码"></el-input>
</el-form-item>
<el-form-item label="SSH密钥:" prop="SSHValue" :data-distinguish="'loginWay' /* DO NOT remove 用来区别不同的form避免报错提示的显示 */">
   <el-select v-model="resetSystemForm.SSHValue" placeholder="请选择密钥">
    <el-option v-for="item in SSHOptions" :key="item.key_id" :value="item.key_id" :label="item.key_name">
     </el-option>
   </el-select>
</el-form-item>
```
当v-if将前一个dom节点销毁时，却没有将错误提示给消除，然后保留给了下一个节点上。
这个问题不知道是element ui的bug还是vue 和element ui 混用就会出现的问题。

- 这个问题的原因出在 vue只会比对一下两个节点内不同的地方进行渲染，所以他会保留之前的错误提示。

竟然如此就要将两个el-form-item进行完全区别，使他们完全不同，就增加了如下东西进行区别： 
```
data-distinguish="'loginWay' /* DO NOT remove 用来区别不同的form避免报错提示的显示 */"
```
这可以避免上面的问题
#学习/elementUI 