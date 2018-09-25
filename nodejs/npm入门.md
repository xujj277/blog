## npm包管理器
 ### 如何使用

**1. npm install**
>npm install -g http-server

-g就是全局的意思 后面就是相应的包
>npm init

会产生package.json
> npm install --save axios
 npm install --save-dev webpack

会把文件放到package.json（相关的信息和所需要安装的依赖都会放到这里，相当于种子的功能，告诉你需要下载什么）中

- --save安装的文件会放到![dependencies](https://upload-images.jianshu.io/upload_images/10142252-8e958100f230413d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- --save-dev安装的会放到![devDependencies](https://upload-images.jianshu.io/upload_images/10142252-08b0252dfa1ae479.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
dev是测试的功能

**2. npm uninstall**
卸载

3. 用.gitignore中写node_modules可以使得上传git的时候不上传这个文件夹

4. package.json
![npm的相应的方法](https://upload-images.jianshu.io/upload_images/10142252-11b5bf62121dd888.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![npm start就会启动http-server](https://upload-images.jianshu.io/upload_images/10142252-7b4ee8bfda2426d2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5. 如果速度慢的时候
>1. npm install -g xxx --registry=https: //registry.npm.taobao.org

nrm一个快速切换源版本的工具
>2. npm install -g nrm
nrm ls
nrm use taobao
nrm use npm

6. n stable 查看最新版本 
sudo n stable
下载一个最新的版本

7. yarn

## npm script
```
{
  "scripts": {
    "css:autoprefixer": "postcss -u autoprefixer -r dist/css/*",
    "css:compress": "csso in.css --output out.css",
    "js:lint": "eslint src/js",
    "js:uglify": "mkdir -p dist/js && uglifyjs src/js/*.js -m -o dist/js/app.js",
    "image:imagemin": "app=imagemin-cli npm run check; imagemin src/images dist/images -p",
    "server": "browser-sync start --server --files 'dist/css/*.css, dist/js/*.js'",
    "watch": "onchange 'src/js/*.js' -- npm run css:compress",
    "start": "npm run server"
  }
}
```
npm run css:autoprefixer
npm start
