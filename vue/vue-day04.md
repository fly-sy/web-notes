## 组件传值 （重点）

### 父传子  

1. 在子组件上，使用v-bind 绑定要传递的数据（数据来至于父组件） <login :msg="msg"></login>

2. 在子组件中，使用props接受传递的数据  props: ['msg']  props: {msg:{type:String}}

props 和data 的区别   

props 只读  

data  可读可写  


### 子传父   


1. 在子组件上，使用v-on绑定要传递的函数（函数来至于父组件） <login :msg="msg"  @show="show"></login>

2. 在子组件中，使用this.$emit()  调用传递过来的函数，调用函数的同时把子组件的数据传入    

this.$emit('show','子组件的数据')


## 2、localStorage 本地存储   

1. localStorage.getItem('cmt')  cmt 是本地存储的名称

2. localStorage.setItem('cmt','')

3. JSON.parse       把 字符串转成对象   

4. JSON.stringify   把 对象转成字符串  

## 路由  （对应关系） （面试点）

1. 前端路由: hash值和组件的对应关系，主要拿来分发页面  

2. 后端路由: 请求路径和处理函数的对应关系 ，主要拿来分发资源 


### 路由的使用方式   

1. 直接使用script标签引入   

2. 模块化开发的引入方式 （学到webpack之后再使用） 


### 路由使用方式1   

1. 使用script引入vue-router包  

2. 定义组件  

3. 实例化路由对象  new VueRouter()

4. 配置路由规则    

5. 挂载路由  

6. 渲染路由（占坑） router-view    点击 router-link    

```
  <div id="app">

    <!-- 6.0 渲染路由 -->

    <!-- to 属性 设置hash值 这个来至于path 定义的 字符串
         tag 设置 router-link 渲染成指定的标签     tag="span"
    -->
    <router-link to="/login" tag="span">login</router-link>
    <router-link to="/register" tag="span">register</router-link>

    <!-- router-view 是用来渲染路由 -->
    <router-view></router-view>
  </div>

  <script>

   const login = {
      template: '<div> login 组件</div>'
    }

    const register = {
      template: '<div> register 组件</div>'
    }

    // 3.0 实例化路由对象   
    var router = new VueRouter({

      // 4.0 定义路由的规则
      routes: [    // arr
        {          // obj  
          // hash 值  
          path: '/login',
          // 注册组件
          component: login
        },
        {          // obj  
          // hash 值  
          path: '/register',
          // 注册组件
          component: register
        }
      ],

      // 高亮的第二种方式   直接设置类的样式名称   
      linkActiveClass: 'mui-active'

    })

    new Vue({
      el: '#app',
      // 5.0 挂载路由  
      //es5   
      // router: router

      // es6 
      router
    })
  </script>

```

### 路由高亮两种方式  (开发的时候使用其中一种就行了)  

1. 设置 .router-link-active  的样式  

2. 直接在路由的构造选项指定 linkActiveClass: '类样式名称'

### 路由的2种传递参数的方式  

1. query   

```
  /login?id=1&name=zs   

  $route.query.id  
  $route.query.name

```

2. params  

```
  /login/id/name   // 这一段是显示在地址栏中的   

  {
    path:'/login/:id/:name'   // 路由规则的占位   
  }  

  $route.params.id  
  $route.params.name

```

### 嵌套路由   


```
<div id="app">

    <!-- 6.0 渲染路由 -->
    <router-link to="/account" tag="span">account</router-link>
    <router-view></router-view>

  </div>

  <template id="account">
    <div>
      <router-link to="/account/login" tag="span">login</router-link>
      <router-link to="/account/register" tag="span">register</router-link>

      <router-view></router-view>
    </div>
  </template>
  <script>

   const account = {
     template: '#account'
   }

   const login = {
      template: '<div> login 组件</div>'
    }

    const register = {
      template: '<div> register 组件</div>'
    }

    // 3.0 实例化路由对象   
    var router = new VueRouter({

      // 4.0 定义路由的规则
      routes: [    
        {
          path: '/account',
          component: account,
          children: [
            {
              path: '/account/login',
              component: login
            },
            {
              path: '/account/register',
              component: register
            }
          ]
        }
      ],

      // 高亮的第二种方式   直接设置类的样式名称   
      linkActiveClass: 'mui-active'

    })

    new Vue({
      el: '#app',
      // 5.0 挂载路由  
      //es5   
      // router: router

      // es6 
      router
    })
  </script>



```


## ref 获取DOM和组件  
1. ref 两个作用  

+ 获取原生的DOM  

+ 获取子组件的data和methods   

2. 如何获取  

+ 在指定的元素上面定义 ref=”myDOM“

+ DOM this.$refs.myDOM.innerText   

+ 组件 this.$refs.myCom.msg    