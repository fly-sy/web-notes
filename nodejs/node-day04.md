# node-day04 

## 一、mac系统和window系统 apache 服务 （了解）

### win  

  + phpstudy    apache服务器  mysql服务器 

  + wamp          apache服务器  mysql服务器 

### mac  

  + mamp        apache服务器  mysql服务器 

## 二、协议、ip、域名、端口、dns服务器 （了解）

+ 协议  https  http

+ ip     192.169.1.1

+ 域名    baidu.com

+ dns服务器   处理 ip 和域名 的对应关系  

+ 端口  可以让一台服务根据端口提供不同的服务    

## 三、node服务器  （重点）

### 原生方式 

```
  1.0 引入http模块
  const http = require('http')

  2.0 创建node服务   

  const server = http.createServer()   

  3.0 监听路径请求   

  server.on('request',(req,res)=>{

    // 处理逻辑
    console.log(1)

    res.end('hello nodejs')
  })

  4.0 给服务设置端口号  

  // 参数1 端口号
  // 参数2 ip 可选  
  // 参数3 callback 回调函数  
  server.listen(3000,()=>{
    console.log('http://127.0.0.1:3000')
  })


  通信模型  

  请求--> 处理 --> 响应  

```

## 四、静态资源服务器 （重点） 

```
const http = require('http')
const fs = require('fs')
const path = require('path')

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


// 静态资源托管  原生方式   express 框架  
function readStaticFile(res, url) {
  fs.readFile(path.join(__dirname, url), (err, data) => {
    if (err) return res.end('404')
    res.end(data)
  })
}
```

## 五、node结合art-template （重点）

### 前端 art-template 

1. 使用script引入art-template

2. var html = template(id,obj)

3. $('xxx').html(html)

### 后端 art-template   

1. 安装 art-template  包

  yarn add art-template -S  

2. 引入art-template  

  const template = require('art-template')

3. 使用 art-template 绑定页面和数据 

  var html = template(abspath,obj) // abspath 是页面所在的绝对路径 

4. 响应给前端 

  res.end(html)

## 六、服务端渲染（SSR）和客户端渲染的对比 （拓展）

http://www.cnblogs.com/sunqq/p/8257243.html 

