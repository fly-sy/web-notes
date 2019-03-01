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
    4. 使用vue、angular、react构建项目

#### 后端  

  1. 编写接口  
    
  2. 调用数据库 

  3. 编写页面逻辑  

  4. 项目的安全性处理  

## 二、 安装nodejs   

  https://nodejs.org  

  ps: 装的node建议直接默认安装  


## 三、执行js文件的2中方式   

1. 使用REPL环境 （不推荐）

2. 使用node命名执行js文件   

  node index.js  

  ps: 文件的目录一定是根目录 

## 四、es6语法   

### 1、let const  

+ let 没有变量的提升，具有{} 块级 作用域   

+ const（定义常量） 没有变量的提升，具有{} 块级 作用域   ，定义之后一定要赋值，并且不能再次的重新赋值  

### 2、解构赋值

  ```
    // 解构对象
    const obj = {
        name: 'fly',
        age: 18
    }

    const {name,age} = obj  

    console.log(name,age)

    // 解构数组  
    let arr = [1,2,3,4] 

    let [a,b,c,d] = arr

    console.log(a,b,c,d)

  ```

### 3、模板字符串  

```

var str = 'fly'

var html = `<div>${str}</div>`    ${} 必须在 ``（tab键上边的~键）里面使用  
```

### 4、padStart padEnd  

```
 padStart(length,str)   // length 填充后的总的长度，str 是使用某个字符串填充  ，在开头的位置进行填充  
 padEnd(length,str)     // length 填充后的总的长度，str 是使用某个字符串填充  ，在结尾的位置进行填充  

```

### 5、函数默认值的使用  

```
  function show(str = 'fly'){
    consoel.log(str)
  }
  show()
```

### 6、解构赋值 + 函数默认值 

```
  function show({x,y=0}){
    return x + y
  }
  show({
    x: 1
  })
```

### 7、 rest参数和 扩展运算符   

+ 在函数定义的时候使用的 ...obj 叫做rest 参数   

+ 在函数调用的时候使用的 ...obj 叫做扩展运算符   

```
  <!-- 参数不确定的时候就需要使用rest参数 -->
  function show(arr){   // 这里的rest 是一个数组   
  }
  var arr = [1,2,3,4]
  show(1,2,3,4)
  show(...arr)   //

```

### 8、箭头函数  

+ 箭头函数其实是一个匿名函数  

+ 箭头函数的this指向永远指向外部的this  

```
  <!-- es5  -->
  var show = function(item){
    return item
  }

  <!-- es6 箭头函数 -->

  const show = (item)=>{
    return item  
  }

  <!-- 最简化的写法 -->
  <!-- 只有一个参数的时候 ()可以省略 方法体只有一行的时候可以省略 {} 和 return -->
  const show = item => item 

  <!-- 多个参数的时候 ()不可以省略 方法体只有一行的时候可以省略 {} 和 return -->
  const show = (x,y) => x + y   

```