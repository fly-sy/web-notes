# node-day07  

##  一、NodeJS中使用mysql   

```
  var mysql = require('mysql');
  var connection = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'root',
    database: 'mydb_12_9'
  });

  var sql = 'select * from users where isdel = 0'
  connection.query(sql, function (error, results, fields) {
    if (error) throw error;
    console.log(results)
  });

```

## 二、使用mysql进行CRUD

## 1、查询   

```
  var sql = 'select * from users where isdel = 0'
  connection.query(sql, function (error, results, fields) {
    if (error) throw error;
    console.log(results)
  });
```

## 2、添加

```
  var obj = {
    username: '666',
    age: 18,
    gender: '女'
  }

  var sql = 'insert into users set ?'

  connection.query(sql, obj, function (error, results, fields) {
    if (error) throw error;
    console.log(results)
  });

```

## 3、更新

```
  var obj = {
    id: 1,
    username: '999',
    age: 18,
    gender: '女'
  }

  var sql = 'update users set ? where id =?'

  connection.query(sql, [obj, obj.id], function (error, results, fields) {
    if (error) throw error;
    console.log(results)
  });
```

## 4、删除
```

  var sql = 'delete users set isdel = 1 where id =?'   

  connection.query(sql, 7, function (error, results, fields) {
    if (error) throw error;
    console.log(results)
  });

```

## 5、软删除 
```
  var sql = 'update users set isdel = 1 where id =?'   // 第2个id 一般是通过请求路径传递回来的  

  connection.query(sql, 7, function (error, results, fields) {
    if (error) throw error;
    console.log(results)
  });

```

## 二、get请求传递数据的2中方式 以及post请求  （重点）  

### 1、query   

  /index.html?id=1&name=fly    

  router.get('/index.html',(req,res)=>{

    console.log(req.query)

  })

### 2、params    

  /index.html/1/fly    

  router.get('/index.html/:id/:name',(req,res)=>{

    console.log(req.params)

  })

### 3、post 数据解析  

+ yarn add body-parser -S  

+ const bodyParser = require('body-parser')

+ app.use(bodyParser.urlencoded({extented:false}))

+ 可以在任意的路由中使用 req.body 获取解析后的参数     


## 三、jsonp和cors的区别 （面试）  

1. jsonp  

  + 只支持get请求  

2. cors 

  + 可以发送正常的ajax请求 

  + 前提是后台开启了cors功能  

3. webpack-dev-server 反向代理   

4. nginx 反向代理  （一般都是后台设置）