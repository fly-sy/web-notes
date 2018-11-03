# node-day03  

## 一、模块化

### 1、什么是模块化  (面试)

  在一个js文件中，引入另一个js文件   

### 2、nodejs为什么需要模块化  

  nodejs 没有页面，只有js文件，如果不能相互引入，nodejs就没有意义    

  ps: nodejs 是 commonJS的实现    

### 3、如何实现模块化  

1. 前端方式 （了解）

    require.js  

    sea.js   

2. 后端方式 

    commonJS 

### 4、commonjs 的特性规范   

+ 引入  require  

+ 暴露  export    

+ 对象  module（是一个标识符） 

  const m1 = module.require('./m1.js') // 导入自己的m1.js模块 module 是可以省略的   

#### global (全局变量、基本不用)

global 只能访问 global 暴露的数据  ，不能访问  export 暴露的数据 

#### export 和 module.export 的区别  

```
  暴露的方式 2 种  

  export.a  =  1    

  module.export.b = 2  

  指向相同的对象  

  export.a  =  1    

  module.export= {
    b: 2 
  }

  指向不同的对象，并以module.export 的对象为主 ，以后为了避免使用错误,推荐使用 module.export = {} 暴露数据  
```

## 二、模块分类  

1. 系统核心模块  

  require('fs')

2. 第三方模块   

  require('jquery')

3. 自定义模块  

  require(相对路径)  


## 三、包 

### 什么是包

  把多个模块结合在一起，放在一个文件夹中，这个文件夹就是包     

### 包的规范  

  + package.json   

  + lib / src 存放源码    

  + dist 存放外界使用的  

  + test 测试文件  

  + doc  文档   

#### package.json 定义规范  

+ name  包的名称  

+ version 版本号  

+ main 包的入口路径  

## 四、包的管理工具 npm、yarn  

1. 安装nrm （全部的镜像源都有）

  npm install nrm -g  

  nrm -V    

  nrm use taobao  把镜像切换到taobao   

  nrm ls  查看切换到那个镜像源  

2. 安装yarn  

  npm install yarn -g     

  yarn -v   

3. cnpm  (这个镜像源只有淘宝的) 中国版的 npm  

  npm install -g cnpm --registry=https://registry.npm.taobao.org

+ 三者取其一 

  npm install jquery -S  

  npm uninstall jquery -S 

  cnpm install jquery -S 

  cnpm uninstall jquery -S 

  今后装包推荐使用 yarn  
  yarn add jquery -S  

  yarn remove jquery -S  

## 六、module.export = add 和 module.export= {add} 的区别

+ module.exports=add  

  直接暴露出一个函数  add  

+ module.exports = { add}  

  暴露的是一个 {add} 


## 七、包的安装  

### 全局包 （工具类的包） 

+ nrm 

+ yarn 

+ cnpm  

+ c:/users/自己的用户/AppData/Roaming/npm/node_modules

### 本地包  

+ npm init -y (没有package.json文件的时候才需要)

+ -S  全写 --save       项目打包上线的时候需要 比如 jquery bootstrap  

+ -D  全写 --save-dev   开发环境需要 比如 less上线的时候不需要使用 

+ ps: 系统的包和第三方包在引入的时候不需要加上node_modules  

+ 第三方包的查找规则    

  先在node_modules 中查找相应的包名  

  在改包中查找package.json   

  在查找main属性对应的文件   

  试运行该文件   