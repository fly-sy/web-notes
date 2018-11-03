# vue-day02    

## 1、品牌案例  

### 添加功能 

1. 先包装一个对象数据  var data = {id:this.id,name:this.name,ctime: new Date()}

2. 定义添加函数并执行数据的添加操作  this.list.push(data)

### 删除功能 

  ```
    1. 通过id 查找索引    
    
    2. 通过splice 删除数组指定的项  

    del(id){

      this.list.some((item,i)=>{

        if(item.id == id){

          this.list.splice(i,1)

          return true  

        }
      })
    }

    del(id){

      var index = this.list.findIndex((item)=>{
        if(item.id == id) return true
      })

      this.list.splice(index,1)
    }
  ```

### 模糊查询  

  ```
    v-for="(item,index) in search(keyword)"


    es5写法
    search(keyword){

      var newArr = []
      // forEach 没有返回值    
      this.list.forEach((item)=>{
        if(item.name.indexOf(keyword) != -1){
          newArr.push(item)
        }
      })

      return newArr 

    }


    es6 写法  
    search(keyword){

      // filter 有返回值 返回的是一个数组   
      return this.list.filter((item)=>{
        if(item.name.includes(keyword)){
          return item 
        }
      })

    }
``` 

## 2、过滤器    

### 全局过滤器  

1. 基本使用

```
  Vue.filter('过滤器名称',callback) 

  {{msg | datafmt('haha','xixi')}}

  // data 是要过滤的数据 

  // arg1 

  // arg2 

  // 参数可以无限使用   
  Vue.filter('datafmt',(data,arg1,arg2)=>{
    // 必须要有return 不然返回undefined 
    return
  }))    
```

2. 使用场景 

+ 插值表达式  

+ 绑定数据过滤    

### 私有过滤器 

```
  new Vue({
    filters: {
      datafmt(data,arg1,arg2){

        return 
      }
    }
  })
```

## 3、自定义修饰符  （一般只用全局的）

Vue.config.keyCodes.键名=对应的键盘码

enter  13  

## 4、自定义指令   

### 全局指令 

```
v-color="'red'"

Vue.directive('指令的名称',{})

<!-- 定义的时候不需要 前缀 v- -->
Vue.directive('color',{
  // el 是绑定的指令的元素的原生DOM
  // binding 是一个对象 可以获取到 指令的值 value 、expression
    
  bind(el,binding){
    // 一般用于操作css样式 ，在内存中使用   
    el.style.color=binding.value
  },
  inserted(el,binding){
    // 一般用于操作DOM， 在DOM加载完毕的时候可以执行一些js    
  },
  updated(el,binding){
    // 多次的更新操作  VNode
  }
})


Vue.directive('color',(el,binding)=>{

})
```

### 私有指令  

```
  new Vue({
    directives: {
      color(el,binding){

      }
    }
  })
```

## 5、Vue 构造函数属性

+ el         string 

+ data       object 

+ methods    object

+ filters    object

+ directives object 

+ created    function 

+ mounted    function   


## 6、vue-resource   


1. this.$http.get(url[,options]).then(callback)

+ url 请求路径

+ 第一个options 一个对象 设置请求的字段   {params:{name:1}}

```
  // 请求参数方式1  
  this.$http.get('http://www.baidu.com',{params:{name:1}})

  // 请求参数方式2  
  this.$http.get('http://www.baidu.com?name=1')

```

2. this.$http.post(url[,options][,options]).then(callback)

+ url 请求路径

+ 第一个options 一个对象 设置请求的字段    {name:name}

+ 第二个options 一个对象 设置表单的请求格式  {emulateJSON:true}

```
  this.$http.post('http://www.baidu.com',{name:1},{emulateJSON:true})
```


3. this.$http.jsonp(url[,options]).then(callback)

+ url 请求路径

+ 第一个options 一个对象 设置请求的字段   {params:{name:1}}

```
  // 请求参数方式1  
  this.$http.get('http://www.baidu.com',{params:{name:1}})

  // 请求参数方式2  
  this.$http.get('http://www.baidu.com?name=1')

```

## 7、 vue-resource 全局配置  

+ Vue.http.options.root = '' 设置根路径    

+ Vue.http.options.emulateJSON = true  

## 8、jsonp 请求原理  

1. 在前端定义一个方法体   

2. 通过script标签把方法体的名称传递给后台  callback 设置传递的方法名    

3. 后台在接受到方法体的名称之后，调用并传递数据   

4. 这个时候前端的方法体，就可以使用一个参数接受后台传递过来的数据   
