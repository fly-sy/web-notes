# node-day02  

## 一、fs模块 

### fs.readFile(path[,options],callback)

+ path 读取路径 

+ options 可选参数 默认为 null    

+ callback 读取文件的回调函数  err,data  

+ 示例 

  ```
    // 1.0 引入fs模块 

    const fs = require('fs')

    // 2.0 读取文件 

    fs.readFile('./files/1.txt','utf-8',(err,data)=>{

      if(err){ return console.log(err.message)}

      console.log(data)
     
    })
  ```

### fs.witerFile(path,data[,options],callback)

+ path 读取路径 

+ data 要写入的数据 

+ options 可选参数 默认为 utf-8  

+ callback 读取文件的回调函数  err

+ 示例 

  ```
    // 1.0 引入fs模块 
  
    const fs = require('fs')
  
    // 2.0 读取文件 
  
    fs.witerFile('./files/2.txt','ssssss',(err)=>{
  
      if(err){ return console.log(err.message)}
  
      console.log('写入成功')
    })
    
    ps: 写入的文件会覆盖之前的内容
  ```

### 复制文件 

#### 传统方式  

```
  复制思路  

  1.0 先使用 readFile 读取某个文件

  2.0 再使用 writeFile 把读取的内容写入到另一个文件中  

```

#### fs.copyFile(src, dest[, flags], callback)

+ src 拷贝的文件源

+ dest 拷贝到那个文件   

+ flags 可选 是否拷贝  

+ callback 拷贝的回调函数   err  

```
  // node 需要时 v8.5 以上的
  const fs = require("fs");

  // 默认情况下，destination.txt 将创建或覆盖
  fs.copyFile("./files/1.txt", "./files/1 - copy.txt", err => {
    if (err) throw err;
    console.log("source.txt was copied to destination.txt");
  });

```

### fs.appendFile(path, data[, options], callback)

```
  fs.appendFile('message.txt', 'data to append', (err) => {
    if (err) throw err;
    console.log('The "data to append" was appended to file!');
  });
```

## 二、path模块   

### path.join(path)

```
  __dirname + 'files/1.txt'

  const path = require('path')

  path.join(__dirname,'./files/1.txt')
  
  ps: 以后涉及到路径拼接的时候  尽量使用path模块 
```

## 三、 __dirname 、__filename 路径

+ __dirname  

  /Users/fly/Desktop

+ __filename  
  /Users/fly/Desktop/001.js 


## 四、单线程和多线程 （了解）

https://blog.csdn.net/hr10230322/article/details/78642898 

## 五、nodejs的异步同步  

+ 异步不会阻塞后面的代码

+ 同步会阻塞后面的代码

+ ps：一条线程先执行同步的代码后执行异步的代码，nodejs中推荐使用异步操作  

https://blog.csdn.net/qq_21033663/article/details/51564786

