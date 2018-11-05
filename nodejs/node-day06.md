# node-day06  

## 一、中间件  

### 1、什么是中间件  (面试) 

+ 中间件是路由的处理函数    

+ 这个处理函数有三个参数 req、res、next ， next 是一个函数    

+ 中间件必须使用  use 调用    

### 2、中间件的定义    

```

  function middle(req,res,next){

    next()
  }

  app.use(middle)
```


### 3、 第三方中间件 body-parser  （重点）

+ yarn add body-parser -S   

+ const bodyParser = require('body-parser')

+ app.use(bodyParser.urlencoded({extended:false}))


### 4、中间件分类  (记忆)

#### 应用级中间件： 挂载在app上的  

```
  app.use((req,res,next)=>{

  })
```

#### 路由级中间件： 挂载在router上的 

``` 
  router.get() 

  router.post()
```

#### 错误处理中间件： 必须带有err，req,res,next  

```
  app.use((err,req,res,next)=>{

  })
```

#### 内置中间件： express.static() 现在唯一一个内置的中间件  

#### 第三方中间件   

+ body-parser   

+ express-session   

+ ...  
 


## 二、模块查找规则  

### 1、核心模块 

+ 默认先从缓存中查找   

+ 在本地引入查找，找到了之后再缓存起来  

### 2、自定义模块   

+ 默认先从缓存中查找   

+ 查找的循序    

  index --> index.js --> index.json --> 二进制文件  

### 3、第三方模块  

+ 默认先从缓存中查找   

+ 查找的循序 

  自定义包  
  
    先查找文件夹  --> package.json --> main --> 指定的文件  

  第三方模块  
   
    node_modules -->  先查找文件夹  --> package.json --> main(试图运行index.js) --> 指定的文件 