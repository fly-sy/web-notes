# vue-day05.md

## 1、methods、watch、computed 的区别   

### methods (属性计算的时候不推荐使用)  

+ methods定义的函数只能监听DOM数据元素的变化，不能监听地址栏的变化  

+ 目标: 实现一些业务逻辑  

### watch  （监听路由变化）

+ watch 既可以监听DOM数据的变化，也可以监听地址栏的变化

+ 目的: 主要是用来监听路由的变化  


### computed  （计算属性）

+ 注意1： 计算属性，直接把方法名当做data中的属性使用

+ 注意2： 只要 计算属性，这个 function 内部，所用到的 任何 data 中的数据发送了变化，就会 立即重新计算 这个 计算属性的值

+ 注意3： 计算属性的求值结果，会被缓存起来，方便下次直接使用； 如果 计算属性方法中，所以来的任何数据，都没有发生过变化，则，不会重新对 计算属性求值

+ 目标: 主要目的用于计算属性 


## 2. 包管理工具 nrm 、cnpm 和 yarn 安装使用 (执行这些命名需要先装node) 

### nrm 

1. npm install nrm -g   全局安装只需要安装一次  

2. nrm --version    测试版本  

3. nrm use (镜像的名字) npm、cnpm、taobao（建议使用taobao）  把国外的镜像切换成国内   （安装速度会提高）

4. nrm test 查看切换到那个镜像源   

5. nrm list(ls) 查看可切换的镜像源

### cnpm  (装包的时候不建议使用这个，装的包很恶心)

+ npm install -g cnpm --registry=https://registry.npm.taobao.org

### yarn  

+ npm install yarn -g   (全局安装)

+ yarn -v   测试版本    

+ yarn add vue -S      安装包

+ yarn remove vue -S   删除包  

+ yarn  根据package.json 安装所有的依赖包    

### npm   

+ npm install vue -S  

+ npm uninstall vue -S  

+ npm install  根据package.json 安装所有的依赖包    

### -g -S -D 的区别  

-S  全写 --save

装在本地的上线环境

-D  全写 --save-dev  

装在本地的开发环境  

-g  当做工具来使用（只需要装一次，只要你的电脑没有中毒xxx,基本上可以一直使用） 

## 是前端资源模块化管理和打包工具

+ less --> css

+ 文件打包  通过webpack 把类似 jquery、vue 打包成 build.js  

+ 文件压缩  

+ 路径处理  

+ 模块化  

+ 快速构建项目   

+ ps： 把项目使用到的一些资源转换成浏览器认识的资源  


