# node-day01 

## 一、前端和后端开发的区别    

### 1、传统的开发模式   

#### 前端

  1. 静态页面  

  2. js动画效果，jquery 

  3. 处理一些文件    

  4. 可能都不涉及到ajax请求  

#### 后端

  1. 编写接口  
  
  2. 调用数据库 

  3. 编写页面逻辑  

  4. 项目的安全性处理  

  5. 把前端的页面整合到.jsp 、.aps、 .php  ajax  

### 2、前后分离开发模式  

#### 前端

  1. 页面的编写  

  2. 动画效果的实现 、jquery、css3（animate.css）

  3. 使用ajax 请求后台的接口，并把数据渲染到页面中 （art-template）  

#### 后端  

  1. 编写接口  
    
  2. 调用数据库 

  3. 编写页面逻辑  

  4. 项目的安全性处理  

## 二、 安装nodejs   

  https://nodejs.org  

  ps: 装的node建议直接默认安装  


## 三、执行js文件的2中方式   

1. 使用REPL环境 （不使用）

2. 使用node命名执行js文件   

  node index.js  

  ps: 文件的目录一定是根目录 

## 四、es6语法   

### 1、默认参数    

#### 传统方式 
```
  function show(str){
    var str = str || ''
  }

```

#### es6方式   

```
  function show(str=''){
   
  }

```

### 2、解构赋值     

#### 解构对象

```

  var obj = {
    name: 'fly'
    age: 18
  }

  // 一般情况下没有必要重新定义一下名称  
  var {name,age:age2} = obj  

  console.log(name,age:age2)

```

#### 解构数组   

```
  var arr = [1,2,3,4]

  var [a,b,c,d] = arr   

  // arr[0] arr[1]
  console.log(a,b,c,d)


  // 解构数组 结合 拓展运算符   
  var arr = [1, 2, 3, 4]

  var [a, ...d] = arr

  console.log(d)

```


### 3、定义变量   

1. let 

2. const   

ps: 都没有变量提升，都具有 {} 作用域，const定义的值不能，重新赋值，并一定在定义的时候赋值  

### 4、字符串的拓展   

#### 模板字符串  

1. ``   

2. 使用${} 给变量占位 

``` 
  var str = 111

  var str2 = 222 

  `${str}000${str2}`

  ps: ${} 必须在 `` 里面使用   
```

#### startsWith 、 endsWith  

判断字符串开头或者结尾是否存在某个字符串 ，返回true 或者false    

#### padStart、padEnd  字符串拼接  

1. padStart(length,str) length 是拼接后的字符串的总长度，str是要使用什么字符串拼接  （开头） 

2. EndStart(length,str) length 是拼接后的字符串的总长度，str是要使用什么字符串拼接  （末尾）


### 5、rest 参数和 拓展运算符   

```

  function show(...rest){       //在函数定义使用的 ...obj 叫做 rest 参数  
    // 使用...rest 那么rest 类型为 数组  
    var result = 0
    rest.forEach((item)=>{
      result += item
    })  

    console.log(result)
  }

  // 参数不确定  
  //show(1,2,3,4)
  var arr = [1,2,3,4]
  show(...arr)  // 在函数调用的时候使用的 ...obj 叫做 拓展运算符     
```


### 6、 箭头函数的使用   

#### es5 方式 

```
  var show = function(item){
    return item 
  }

  console.log('fly')
```

#### es6 方式   

```
 const show = (item) => {
   return item 
 }

 console.log('fly')


 最简化的方式   
 // 只有一个参数的时候 
 
 //（）可以省略 ，方法体只有一行的时候 {} return 可以省略   
 const show = item => item   


 //多个参数   
 // 多个参数不能省略()  
 const show = (x,y) => x + y 

```


### 7、es6对象中简写方式     

```
  var name = 'fly' 

  var age = 18  

  // es5  
  var obj = {
    name: name
    age: age,
    show: function(){

    }
  }

  //es6  
  // es6 对象中key 和value 一致的时候可以只保持一个    
  const obj = {
    name,
    age,
    show(){

    }
  }

```

