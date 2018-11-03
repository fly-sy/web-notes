# node-day05 

## 一、 express  

### 1、express的基本使用  (重点)

```
  装包  

  yarn add express -S   

  // 1. 导入 express 模块
  const express = require('express')

  // 2. 创建服务器
  const app = express()

  // app.get 表示，只监听 get 类型的请求
  // app.post 表示，只监听 post 类型的请求
  // app.all    表示，监听所有类型的请求
  app.get('/', function (req, res) {
    // 这里，我们使用 的 res.end 是原生 Node 提供的 API
    res.send('试试就试试123')
  })

  //    /index.html

  //    /movie.html

  app.listen(4000, () => {
    console.log('express server running at http://127.0.0.1:4000')
  })

```

### 2、静态资源托管   

#### 原生静态资源托管 

```
  const http = require('http')
  const fs = require('fs')
  const path = require('path')
  const mime = require('mime')

  const server = http.createServer()

  server.on('request', (req, res) => {
    // 拿到请求的类型
    const method = req.method.toLowerCase()
    // 拿到请求的地址
    const url = req.url
    // 因为 我们浏览器请求的  URL地址，已经和 服务器上，文件的物理路径，对应上了；

    // 静态的资源都是 什么请求方式  ？  get   
    readStaticFile(res, url)
  })

  server.listen(3000, () => {
    console.log('http://127.0.0.1:3000')
  })

  // 封装静态资源托管函数   
  function readStaticFile(res, url) {
    fs.readFile(path.join(__dirname, url), (err, data) => {
      if (err) return res.end('404')
      res.end(data)
    })
  }
```

#### express静态资源托管  （核心）

```
  const express = require('express')

  const app = express()

  // 使用 express.static 来托管 views 目录

  // 第一个/assets 是标识符，用于服务器路径的拼接
  // 第二个assets  是文件夹，指定需要托管的静态资源文件  
  app.use('/assets',express.static('assets'))     

  //127.0.0.1:3000/style.css    
  //127.0.0.1:3000/assets/style.css    
  app.use(express.static('views'))  // 使用express 托管的文件夹不能再使用到 url 地址中

  app.listen(3000, function () {
    console.log('App listening on port 3000!');
  });

```

## 二、nodemon工具安装 (可以自动刷新服务)

+ npm install nodemon -g   

+ nodemon 要运行的js文件  

  node app.js  改成 nodemon app.js 

## 三、服务器、域名（拓展）

### 云服务器供应商

+ 阿里云服务器  

+ 腾讯云    

### 部署服务器准备  

1. 购物云服务    

  阿里云   

  腾讯云  

  都是需要购买备案    

2. 购买域名      

  万网  

  腾讯  

  也是需要备案  

3. dns解析    

  把域名和自己的服务器的ip绑定在一起   

+ ps: 这些东西都是谁来处理的 ？  

  运维  

  后台

  前端 (告辞)

## 四、模板引擎使用  (重点)

### art-template  

1. yarn add art-template -S   

2. const template = require('art-template')

3. const html = template(abspath,obj)  // abspath 页面的绝对路径 , obj 是要渲染的对象  

4. res.end(html)

### ejs （是nodejs兼容性比较好的）

1. yarn add ejs -s  

2. app.set('view engine','ejs') // 指定使用那个模板引擎    view engine 是写死的不能乱改

3. app.set('views','views')     // 指定模板所在的页面 第一个views 是标识符 固定写死的  ,第二个views 是模板所在的文件夹 （可以改的）

4. res.render('index.ejs',obj)  // 参数1 是模板页面的名称.ejs 可以省略 , obj 是要渲染的对象   

## 五、res常用的函数  （了解） 

+ res.end()      原生 

+ res.json()     返回一个对象，一般是写接口的时候使用 

+ res.redirect() 原生

+ res.render()   使用类似于ejs的时候使用 

+ res.send()     中文乱码 

+ res.sendFile   托管少量的静态资源，以后很少使用 

## 六、路由 （面试）

  路由是一种对应关系  

### 后端路由  

  前端的请求url 和 处理url的函数的对应关系，就叫后端路由  

### 前端路由  （vue）

### 模块化开发的优点

  模块化并不能减少我们的代码量，但是可以使得我们的页面更加清晰，也方便后期的维护 

### express 路由使用  

1. 先引入express  

  const express = require('express')

2. 使用exprss.Router() 创建路由 

  const router = express.Router()  

3. 把处理的对应关系挂载router上   

  router.get('/',callbcak)

4. 在app上注册router  

  app.use(router)