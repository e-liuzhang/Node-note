# 使用Node操作MySQL数据库

## 1 基本使用

安装：

```shell
npm install --save mysql
```

hello world:

```javascript
var mysql = require('mysql');
var connection = mysql.createConnection({
    host     : 'localhost',
    user     : 'root',
    password : '123456',
    database : 'students'
});

connection.connect();

connection.query('insert into users values(null,"admin","123456")', function (error, results, fields) {
    if (error) throw error;

    console.log('The solution is: ', results);
});

connection.query('SELECT * from `users`', function (error, results, fields) {
    if (error) throw error;

    console.log('The solution is: ', results);
});

connection.end();
```

## 2 连接池

使用连接池可以帮助我们更好的管理数据库连接。数据库连接池可以限制连接的最大数量，复用已有的连接等：

```javas
var mysql=require("mysql");
var pool = mysql.createPool({
    host: 'localhost',
    user: 'root',
    password: '123456',
    database: 'students'
});
var query=function(sql,callback){
    pool.getConnection(function(err,conn){
        if(err){
            callback(err,null,null);
        }else{
            conn.query(sql,function(qerr,vals,fields){
                //释放连接
                conn.release();
                //事件驱动回调
                callback(qerr,vals,fields);
            });
        }
    });
};
module.exports=query;
```

调用：

```javas
var query=require("./lib/mysql.js");
query("select 1 from 1",function(err,vals,fields){
 //do something
});
```

