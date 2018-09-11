# express_connect_to_Mysql
在node.js中使用Mysql

## Preface
&emsp;&emsp;最近在看George Ornbo的node.js入门经典，因为书里用的数据库是NoSQL数据库，而平时习惯了关系型数据库，所以就想仿照这本书的模式，自己写一个mysql连接的文档。
## 1 连接Mysql
### a. 利用终端创建一个基本的Express站点：  
&emsp;&emsp;
```cmd
express connect_to_mysql
cd connext_to_mysql && npm install
```
### b. 安装mysql中间件：  
&emsp;&emsp;在这里要说的是，有两种安装方式，一是打开package.json，将mysql依赖模块手动加入，然后再进行npm install：
```json
"dependencies": {
    "mysql": "^2.16.0"
  }
```
&emsp;&emsp;另一种方法就是在npm install命令的末尾加上--save，这样安装完mysql中间件之后会自动将依赖写入json文件。
```cmd
npm install mysql --save
```
### c. 在app.js文件中为应用程序请求Mysql  
```javascript
var mysql=require('mysql');
```
### d. 连接数据库 
&emsp;&emsp;用createConnection方法创建一个表示与mysql数据库服务器之间连接的connection对象，并用connect方法建立连接，并回调一个对错误信息进行反馈的函数。
```javascript
var connection=mysql.createConnection({
  host:'localhost',
  port:3306,
  database:'***',
  user:'root',
  password:'******'
});

connection.connect(function(err){
  if(!err){
    console.log('connected to Mysql');
  }else{
    throw err;
  };
});
```
### e. 确认mysql服务器运行，运行以下命令启动express服务器  
```cmd
npm start
```
### f. 在终端可以看到以下结果  
![](https://raw.githubusercontent.com/chenxing1020/express_connect_to_Mysql/master/result.png)
