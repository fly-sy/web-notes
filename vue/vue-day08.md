# 面试点  

## 1、什么是回调函数  

```
function show(fn){
  var a = 1; 
  fn(a)
}

show(function(x){
  console.log(x)
})

```
ps: 回调函数说白了就是在一个函数中传入另个函数作为参数 ，传入的方法调用的同时可以把 方法体里面的内容传递出来   


## 2、为什么需要回调函数  

```
function show(callback){

  $.ajax({
    success: function(res){
      <!-- return res    -->
      callback(res)
    } 
  })

  //该函数默认返回undefined    
}

show(function(res){
  console.log(res)
})

```
ps:异步请求无法直接返回获取的值，需要借助回调函数辅助返回  


## 3、大量使用回调函数存在什么问题  （回调地狱） 


## 4、如何解决回调地狱  

使用es6 promise 解决 ，并不能减少代码量   


## 5、promise 的概念  


1. promise 是一个构造函数  

2. 这个promise 的函数上有2个 函数   resolve 、reject     

3. promise 的实力有 .then      prototype.then  

4. .then 有2个回调方法  ，方法的调用在哪里   


```
  function show(){
    return new Promise((resolve,reject)=>{
    
    })

  }

  show()
  // 第一个是resolve 的方法体  
  // 第二个是reject 的方法体   
  .then(function(){},function(){})
  .then()
  .then()
  //  异常捕获  
  .catch()   

  
  // catch  和  reject 有什么区别  

  catch 出现异常的时候停止程序，抛出异常  

  reject 不会停止程序， 抛出异常  
```

```
  async function getData(){

    const data1 = await show()
    const data2 = await show()
    const data3 = await show()
  }

  getData()

```
