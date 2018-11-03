# vue-day01  

## 1、什么是vue   

+ 目前最火的前端框架   

+ 引用 mvvm 设计模式

+ 简单、轻量、快捷的框架 

+ 指令 

+ 组件化

+ 模块化  

+ 路由  

## 2、库和框架的区别 

+ 库 

  一些小的功能、可以通过某个库过渡到另一个库  jquery-->zepto   

+ 框架 (vue、express)

  一整套的解决方案、ui、js(ajax)  

## 3、MVC和MVVM的区别  

1. MVC 

  + model （数据库连接）

  + view   (前端页面)

  + controller （逻辑控制）

    router.js / controller.js  

2. MVVM  

  + model (后台请求的数据，自己写的一些死数据)

  + view  （渲染的模板区域）

  + view model （vm） model和view的调度者     


3. ps:  

  + MVC 是站在整个项目的角度考虑  

  +  MVVM 是站在前端项目的角度考虑   

## 4、Vue 构造函数的属性  

## 5、指令   

+ el      string   指定view的渲染区域 

+ data    object   指定model存放的位置

+ methods object   指定函数的存放位置 

### 渲染指令  

1. {{}} + v-cloak

  **v-cloak如果解决页面闪烁问题**   

  + 通过 [v-cloak] :{display:none} 先把指定的元素  v-cloak 隐藏  

  + 当vue加载完毕之后把指定的 v-cloak删除   

2. v-text

3. v-html 

### 属性绑定

1. v-bind 简写  :  

2. v-model  
  
  + vue中唯一一个双向数据绑定指令

  + 使用场景 (表单元素和组件中使用)

### 单向数据绑定和双向数据绑定的区别  

1. 单向数据绑定

  model改变view改变，不能反过来

2. 双向数据绑定  

  model改变view改变、反之亦然  

### 事件绑定 和 事件修饰符

1. 事件绑定
  
  +  v-on 简写 @   

2. 事件修饰符

  + stop 阻止事件冒泡

  + prevent 阻止默认行为

  + capture 事件捕获 

  + self 只阻止自己的事件

  + once 只阻止一次的默认行为    


### 样式绑定指令   

1. class  （推荐方式）

  + 普通数组   :class="['red','blue','active']"  red、blue、active 都是在css里面定义好的 

  + 数组三元   :class="['red','blue', flag?'active':'']" flag 是在data里面定义好的布尔值  

  + 数组对象   :class="['red','blue', {active:flag}]" flag 是在data里面定义好的布尔值  

  + 对象方式   :class="{red:true,blue:true}" 对象里面的样式名可以用引号包含   key:value  key是样式名 value 是布尔值  

2. style  （几乎不用）

  + 对象  :style="{color: red}"

  + 数组  :style="[{color:red},{width:50px}]"

### 数据遍历  

1. v-for  

  + 普通数组  

  + 数组对象

  + 对象

  + 数字   


2. 标准写法   

  v-for="item in arr" :key="item.id"

  v-for="(item,index) in arr" :key="item.id"

  v-for="(val,key) in obj" :key="key"

  v-for= "counnt in 8" 索引是从1开始到8   

### v-show、v-if   

1. 区别

  + v-show 是通过样式操作元素的显示隐藏 

  + v-if 是通过DOM操作元素的添加删除   

2. 使用场景  
  
  + 如果操作的DOM是少量用哪个都一样 

  + 如果大量操作使用DOM建议使用v-show

  + 频繁点击的也建议使用v-show  






