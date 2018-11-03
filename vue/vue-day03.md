# vue-day03  

## 1、vue 动画三种方式

### 原生css

1. 上半场

+ v-enter        起点

+ v-enter-to     上半场的终点

+ v-enter-active 上半场的时间

2. 下半场   

+ v-leave         下半场的起点

+ v-leave-to      终点

+ v-leave-active  下半场时间

```
  1. 先用transition标签包含要执行动画的元素  

  2. 编写动画样式   


  .v-enter,
  .v-leave-to {
    opacity: 0;
  }

  .v-enter-active,
  .v-leave-active {
    transition: all .8s ease
  }


  <input type="button" value="toggle" @click="flag=!flag">

  <transition>
    <div v-show="flag">显示隐藏</div>
  </transition>


```  

### vue结合animate.css   

1. 引入animate.css 

2. 在transition绑定指定的样式     

``` 
  enter-active-class   进场动画样式
  leave-active-class   离场动画样式
  :duration            设置动画的时间   :duration="number"  :duration="object"  设置的时间不要超过1000  

  <transition enter-active-class="fadeInRight" enter-active-class="fadeOutRight">
    <div v-show="flag" class="animated"></div>
  </transition>

```

### 半场动画   

+ @before-enter="beforeEnter"

+ @enter="enter"

+ @after-enter="afterEnter"

```
 beforeEnter(el, done) {
  // beforeEnter 表示动画入场之前，此时，动画尚未开始，可以 在 beforeEnter 中，设置元素开始动画之前的起始样式
  // 设置小球开始动画之前的，起始位置
  el.style.transform = "translate(0, 0)"

},
enter(el, done) {
  // 这句话，没有实际的作用，但是，如果不写，出不来动画效果；
  // 可以认为 el.offsetWidth 会强制动画刷新x
  el.offsetWidth  // 手动刷新动画  
  // enter 表示动画 开始之后的样式，这里，可以设置小球完成动画之后的，结束状态
  el.style.transform = "translate(150px, 450px)"
  el.style.transition = 'all 1s ease'

  // 这里的 done， 起始就是 afterEnter 这个函数，也就是说：done 是 afterEnter 函数的引用
  done()
},
afterEnter(el) {
  this.flag = !this.flag  
}

```



## 2、 列表动画   

1. 使用transition-group 包裹指定列表元素    

2. v-for 必须结合  :key 使用  key的值不要使用索引，建议使用item.id   

3. transition-group 属性设置  

+ tag 设置 transition-group(默认是span标签) 渲染为指定的标签  如： tag="ul"

+ appear 设置打开页面就有动画效果      

4. 设置删除过渡效果 

```
  .v-move {
    transition: all 0.6s ease;
  }
  .v-leave-active{
    position: absolute;
  }
```  

## 3、组件化和模块化的区别 

+ 组件化: 是在ui的角度，把相同的业务功能当成组件，方便后期的复用，和数据的传递   

+ 模块化: 是在js逻辑角度，把功能抽离成一个个模块，在一个js文件中引入另一个文件就是模块化，方便后期的维护使用

## 4、组件  

### 创建组件的步骤  

1. 定义组件  

2. 注册组件(全局Vue.component、私有components)

3. 渲染组件  

### 全局组件

1. 创建组件方式1（定义和注册分离）

```
  1.0 定义组件
  const login = Vue.extend({
    template: '<div> <h1>haha</h1> </div>'
  })


  /*const login = {
    template: '<div> <h1>haha</h1> </div>'
  } */

  2.0 注册组件
  Vue.component('login',login)

  3.0 渲染组件  
  <login></login>
```

2. 创建组件方式2 (定义和注册结合)

```

  1.0 定义和注册结合
  Vue.component('login',{
    template: '<div> <h1>haha</h1> </div>'
  })

  2.0 渲染组件  
  <login></login>

```

3. 创建组件方式3 (抽离模板)

```
  定义组件的模板  
  <template id="template">
  <!-- 给模板提供一个跟的元素  -->
    <div> 
      <h1>haha</h1> 
    </div>
  </template>

  1.0 定义组件  

  const login = {
    template: '#template'
  }

  2.0 注册组件（全局）
  Vue.component('login',login) // 第一个login是组件的名称 ，第二个是定义组件的返回值  

  3.0 渲染组件  
  <login></login>

  ps: 这三种方式都是全局的组件，建议使用第三种定义方式
```


### 私有组件  

```
 定义组件的模板  
  <template id="template">
    <div> 
      <h1>haha</h1> 
    </div>
  </template>

  1.0 定义组件  

  const login = {
    template: '#template'
  }

  2.0 组件注册（私有）  
  new Vue({
    components: {
      login: {
         template: '#template'
      }
    }
  })

  3.0 渲染组件  
  <login></login>

```

## 5、子组件中定义data 的三种方式   

1. es5  

```
  data: function(){
    retrun {
      msg: 'sss'
    }
  }

  ps: 组件中的data设置成function 是为了确保每一次返回出来的都是一个新的对象   
```

2. es6 

```
  data(){
    retrun {
      msg: 'sss'
    }
  }
```

3. es5 + es6箭头函数    

```
  data:()=>({
    msg: 'sss'
  })

```

## 6、组件切换+动画  

```
<a href="" @click.prevent="comName='login'">登录</a>
<a href="" @click.prevent="comName='register'">注册</a>

// mode 设置动画的模式   
<transition mode="out-in">
  <!-- 指定要渲染的组件 -->
  <component :is="comName"></component>
</transition>

Vue.component('login', {
  template: '<h3>登录组件</h3>'
})

Vue.component('register', {
  template: '<h3>注册组件</h3>'
})

```

## 7、组件的渲染方式

1. 直接使用组件名称渲染

2. 使用component渲染    

+ :is  设置要渲染的组件   

## 8、vue提供的组件和标签  

+ component 渲染切换组件 

+ template 定义组件的模板 

+ transition 单一动画

+ transition-group 列表动画  



## 9、Vue 构造函数的属性  

+ el 

+ data

+ methods 

+ filters 

+ directives   

+ created  

+ mounted   

+ components   

+ props (子组件中的属性)  props: ['msg']   props: {msg:{type:String}}

## 10、组件传值 

### 父传子   

1. 在子组件上使用v-bind 绑定要传递的数据   

2. 在子组建中使用props 接受传递过来的数据  


## 服务器    

+ 数据库服务器   mysql   

+ 语言服务器  php(apache)、java(Tomcat)、node(自己搭建的服务器用命令运行)

+ navicat  数据库的一个界面工具  