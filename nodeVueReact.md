# node

- 安装node环境（node官网安装维护版本）
- npm install gulp（查看版本号：cmd--->node -v）
- 写一份gulpfile.js配置gulp的参数，gulp命令执行监事来完成代码处理（压缩，重命名）

## node (introduce)

> [安装教程]（http://www.runoob.com/nodejs/nodejs-install-setup.html）

- Node.js是一个基于`Chrome V8 `引擎的JavaScript运行时
- node相当于浏览器的控制台（`Chrome V8 `引擎）

## 前端（浏览器）

- 要运行JS，必须借助于HTML文件，没有HTML文件和浏览器环境的话，JS是无法运行的。
- 要有HTML文件，也必须要有浏览器环境。
- 浏览器=界面+控制台
- 此时JS是必须运行在浏览器上，所以只能控制浏览器

## 后端（服务器端）

- 要运行JS，既不需要HTML文件，也不需要浏览器环境，只需要Node环境，node替代了HTML文件，也替代了浏览器
- 服务器（node）=控制台
- JS有了node环境，可以运行在非浏览器环境下，因为node是装在系统上，所以JS可以操作系统
- node（浏览器的控制台===Chrome的V8引擎）



## 运行JS

- 写一份JS代码
- 在该文件夹中打开cmd控制台，或在cmd中定位到该文件的位置
- 在命令行运行命令 `node JS文件的名字.js`



# 模块化

## 自定义模块化

### 前端

- 写多条`<script>引入js`在html中分开引入

```html
<script src="jquery，js"></script>
<script src="cookie.js"></script>
```

### node（后端）

- 没有html，所以需要借助两个JS方法

  - 导出借助于 `module.exports = {(fn),(fn)}`

  ``` js
  function plus(a, b) {
  	return a + b
  }
  
  function sub(a,b){
  	return a-b
  }
  
  module.exports = {
  	plus,
  	sub
  }
  ```

  - 导入，借助于`require`,建议使用相对路径

  ``` js
  var tool = require("./plus.js");
  ```

  ## 内置模块

  > node环境自带，可以直接引入。具体参考 [node官网内置模块API文档](https://nodejs.org/dist/latest-v8.x/docs/api/)

  - Node作为PHP的一种替代（多一种可选方案），PHP能做的，Node也能做。

| 模块       | 名字 |
| ---------- | ---- |
| 读写文件   | fs   |
| 创建服务器 | http |
| 查看系统   | os   |
| 压缩文件   | zip  |
| ...        | ...  |



# HTTP-超文本传输协议

> 前端最多的就是ajax（http协议的一种前端实现方案）

#### GET/POST区别

| GET          | POST         |
| ------------ | ------------ |
| 参数在url上  | 参数在请求体 |
| 有可能有长度 | 没长度限制   |
| 不安全       | 安全         |

#### status（状态码）

状态码    1xx  开始执行  2xx  成功  3xx  重定向  4xx  客户端错误,浏览器端  5xx  服务端

| 状态码 |                                                    |
| ------ | -------------------------------------------------- |
| 1xx    | 开始执行                                           |
| 2xx    | 成功（从服务器请求）                               |
| 3xx    | 重定向（从浏览器之前缓存的数据中请求）----也是成功 |
| 4xx    | 客户端错误（浏览器端）---前端                      |
| 5xx    | 服务端错误（后端）                                 |

### wamp 集成环境

```
window
Apache
MySQL
PHP
```

### 创建服务器

``` js
var http = require('http');
// 该querystring模块提供用于解析和格式化URL查询字符串的实用程序。
var querystring = require('querystring');
var url = require('url');
var fs = require('fs');
var server = http.createServer(function(request, response){
    // console.log(request);
    // 打印request,即得知从前端请求得到什么。
    // 可知，前端输入的userna：123 passwor：123。
    // 此时打印台出现的为一个对象，其中url：'/?username=123&password=123'
    // 因此我们现在要获取到这个url
    console.log(request.url);
    // cmd-------> /?username=123$password=123
    // console.log(url.parse(request.url));
    // cmd-------> search:'?usename=123$password=123'
    //             query:'usename=123$password=123'
    var query = url.parse(request.url).query;
    // 用querystring.parse方法将query解析成对象
    var param = querystring.parse(query);
    console.log(param);
    // cmd-------->{username:'123',password:'123'}
         
    // 为隐式标头设置单个标头值。
    response.setHeader("Access-Control-Allow-Origin","*");
    // 在添加了响应头后，，浏览器控制台---network----Heaher可以看到---Response Heahers
    response.end("hello world");
    // response.end()此方法向服务器发出信号，表明已发送所有响应标头和正文; 该服务器应该考虑此消息完成。必须在每个响应上调用该方法

});

// sever.listen(写端口名，范围：0-65535)
server.listen(8888);
// ----------->在浏览器中localhost：8888，页面呈现：hello world
console.log("启动服务器");
// -----------> cmd ------>启动服务器


// 修改代码后再在控制台启动一下。
// 可以先  ctrl+C  再运行一次命令
```

#### 出现跨域，加一个头部解决

``` js
header("Access-Control-Allow-Origin:*")
```

## 第三方模块

> 可以从[npm](https://www.npmjs.com/)包管理中心下载第三方包，在本地node平台实现自己的一些功能。（gulp就是一个常用的第三方模块）

### 安装

> 建议在根目录下安装

``` bash
npm install xxx(gulp) -g//-g表示全局安装
或者 npm i

添加包时，输入：
cnpm install cheerio --save-dev   
（表示把该模块保存在package.json里的devDependencies里面）
```

建议安装cnpm替代npm，在命令行上输入：

``` bash
npm install -g cnpm --
registry=https://registry.npm.taobao.org
```

- 除了全局安装之外，安装任何包都会被安装在该目录下`node_modules`
- 【注意】该文件夹不要传到svn和git服务器上，当移植这个项目的时候只要用`package.json`描述文件去代替`node_modules`
- 这份文件记录着你开发node的一些关键信息，比如你安装过什么模块作为依赖（可在package.json中查看）

### 卸载

```bash
npm uninstall xxx  //卸载某个模块
npm uninstall //全部卸载
```

### 初始化

>生成一份`package.json`描述文件

```bash
npm init
```

### 使用第三方模块

```js
var request = require('request');
var gulp = require('gulp');
```



# node.js参考教程

> [runoob菜鸟教程](https://www.runoob.com/nodejs/nodejs-tutorial.html)

## 异步

### 前端（浏览器端）

前端异步只有以下几种情况

```
ajax xmlhttprequest
setInterval/setTimeout
jsonp
```

### 后端（服务器端node）

后端异步比前端多很多，很多方法都是异步，可以参考 [node官网内置模块API文档](https://nodejs.org/dist/latest-v8.x/docs/api/)，其中有待Sync的为同步。如：

```js
 fs.readFile //异步
 fs.readFileSync //同步
```

- 异步一般配合回调函数
- 异步非阻塞，相对不稳定，配合回调函数才有意义
- 同步没有回调函数；
- 同步阻塞，相对稳定，不需要回调函数；

```js
//同步
var data = fs.readFileSync('./test.txt');
console.log(data.toString());

//异步
fs.readFile('./test.txt',function(err,data2){
	console.log(data2.toString());
});
```

## 回调嵌套

> #### 用promise解决

```js
//回调嵌套金字塔（后期维护起来特别麻烦）
// setTimeout(()=>{
//     console.log("买披萨");
//     setTimeout(()=>{
//         console.log("喝水");
//         setTimeout(()=>{
//             console.log("玩手机");
//         }), 1000)
//     }, 1000)
// }, 1000)

//利用promise解决这个问题
function buyPizza(){
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            console.log("买披萨");
            resolve();
        }, 1000);
    })
}

function drink(){
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            console.log("喝水");
            resolve();
        }, 1000);
    })
}

function eat(){
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            console.log("吃");
        }, 1000);
    })
}

// 使操作步骤按以下顺序执行
buyPizza().then(drink).then(eat);


// 如果使用Promise.resolve()启动Promise，则在需要传递的参数前面加return即可。
// 如果是利用Promise包装了任务，则把想要传递给下一个task的参数传入resolve()即可。
```

## Promise

### 基本用法

> 以下来自于网络，仅供参考

ES6规定，Promise对象是一个构造函数，用来生成Promise实例

```js
const promist = new Promise(function(resolve,reject){
    if(/*异步操作成功*/){
        resolve(value);
    }else{
        reject(error);
    }
})
```

- `resolve`函数的作用是，将Promise对象的状态从“未完成”变为“成功”（即从 `pending` 变为 `resolved`），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；
- `reject`函数的作用是，将Promise对象的状态从“未完成”变为“失败”（即从 `pending` 变为 `rejected`），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。

Promise 实例生成以后，可以用then 方法分别指定resolved状态和rejected状态的回调函数。

```js
promise.then(function(value){
    //success
    },function(error){
        //failure
        });12345
```

例子:

```js
function timeout(ms){
    return new Promise((resolve,reject)=>{
        setTimeout(resolve,ms,'done');
    });
}
timeout(100).then((value)=>{
    console.log(value);
});12345678
```

```js 
let promise = new Promise(function(resolve,reject){
    console.log('Promise');
    resolve();
});
promise.then(function(){
    console.log('resolved');
});
console.log('Hi!');

//Promise
//Hi!
//resolved123456789101112
```

```js 
//异步加载图片
function loadImageAsync(url){
    return new Promise(function(resolve,reject){
        const image = new Image();
        image.onload = function(){
            resolve(image);
        };
        image.onerror = function(){
            reject(new Error('error');
        };
        image.src = url;
    });
}12345678910111213
```

下面是一个用Promise对象实现的 Ajax 操作的例子。

```js 
const getJSON = function(url) {
  const promise = new Promise(function(resolve, reject){
    const handler = function() {
      if (this.readyState !== 4) {
        return;
      }
      if (this.status === 200) {
        resolve(this.response);
      } else {
        reject(new Error(this.statusText));
      }
    };
    const client = new XMLHttpRequest();
    client.open("GET", url);
    client.onreadystatechange = handler;
    client.responseType = "json";
    client.setRequestHeader("Accept", "application/json");
    client.send();

  });

  return promise;
};

getJSON("/posts.json").then(function(json) {
  console.log('Contents: ' + json);
}, function(error) {
  console.error('出错了', error);
});
```

## request

> 前端请求，具体参考[request模块文档](https://www.npmjs.com/package/request)

任何前端请求都有请求头、请求体、响应头（这是三个用户不可见），响应体（用户可见）。

- 请求头（浏览器信息）
- 请求体（POST请求，请求参数会在这个请求体里）
- 响应头（服务器信息）
- 响应体（页面的内容，用户可见）

## 爬虫

> 爬取网站的内容，可以保存到本地，或者分析页面获取有价值的信息。
>
> 但是，并非所有网站都是能爬，有些网站是防爬虫，还有一些网页是前端JS动态生成

```js
var request = require('request');
var fs = require('fs');
request('https://haiwai.ibaotu.com', function(error, response, body){
    // Print the error if one occurred如果发生错误，请打印错误 
      console.log('error:', error); 
     // Print the response status code if a response was received如果收到回复，请打印响应状态代码
      console.log('statusCode:', response && response.statusCode);
     // Print the HTML for the Google homepage.打印Google主页的HTML。 
      console.log('body:', body);
      // 将爬取到的网站信息保存到./massage.html里
      fs.writeFile('./massage.html', body, function(){
        console.log('网页成功保存');
      })
    }) ;
console.log("开始请求");
```

## cheerio

> 实现网页内容分析，用法类似于jQuery，node版本jQuery,可以用它爬取文字，图片，音频
>
> 参考[cheerio使用文档](https://www.npmjs.com/package/cheerio)

```js
// 爬虫酷狗音乐

var request = require('request');
var cheerio = require('cheerio');
var fs = require('fs');
//1、首先请求到歌手页面
request('http://www.kugou.com/yy/singer/home/1574.html', function(error, response, body) {
    //console.log('body:', body); // Print the HTML for the Google homepage.
    const $ = cheerio.load(body);
    $(".song_hid").each((i,e)=>{
        // console.log($(e).attr("value"));
        var src = $(e).attr("value").split("|")[1];//裁剪得到hash值
        // console.log(src);
         
        // 2、利用hash值再次请求得到歌曲信息
        request('http://www.kugou.com/yy/index.php?r=play/getdata&hash='+src,function(error, response, body){
            // console.log(JSON.parse(body).data.play_url);
            var playUrl = JSON.parse(body).data.play_url;//得到歌曲路径
            // console.log(JSON.parse(body).data.audio_name);
            var audioName = JSON.parse(body).data.audio_name;//得到歌曲名字
            request(playUrl).pipe(fs.createWriteStream('./music/'+audioName+'.mp3'))//下载数据流到./music文件夹下
        });
    })
});
console.log("开始请求");
```

# express

> [npm的express文档](https://www.npmjs.com/package/express)

- 切换不同的路由，会进入不同的逻辑

- 也就是浏览器输入不同的路径，页面就有不同的返回结果

  ```js
  var express = require('express');
  var app = express();
  
  //''路径不同，跳转的页面不同---->路由
  app.get('/', function (req, res) {
    res.send('Hello World');
  })
  
  app.get('/home', function (req, res) {
    res.send('Hello World');
  })
   
  app.listen(3000);
  ```

# express的脚手架

> [npm的express文档](https://www.npmjs.com/package/express)中的**Quick Start**

- 全局安装

```bash
npm install -g express-generator@4
```

### 创建应用结构

> 在一个文件夹(在需要创建路由的目录中)中用`express` 命令创建应用架构

- 自动创建文件

```bash
express test(test是文件名)
cd test(进入到test文件夹，进入下一步)
```

- 进入test文件夹安装其他依赖文件，

```bash
cd test
npm install
或者：cnpm install  //建议使用cnpm安装所有依赖
```

- 启动应用,这样就初始化完成了一个最简单的express项目

```bash
SET DEBUG=test:*  //【注意，要把test改成与自己一开始设置的文件名相同】
npm start
```

- 访问在浏览器的3000端口号

``` js
http://localhost:3000
```

### 创建路由

- 进入创建的test目录下的routes文件夹，复制一份`user.js`到新建的`home.js`文件里，改变`/home`的路径

``` js
var express = require('express');
var router = express.Router();
router.get('/home', function(req, res, next) {
  res.send('hello world');
});
module.exports = router;
```

- 在`app.js`添加以下两条，完成该路由的创建

``` js
var homeRouter = require('./routes/home');//备注：表示当前文件夹下的routes目录下的home.js文件
//code
app.use('/test', homeRouter);
```

- 访问该路径

``` js
http://localhost:3000/test/home
```

## MySQL

> express的脚手架之一，用于与数据库连接
>
> [ 参考文档 ](https://www.npmjs.com/package/mysql)

#### 案例：注册

- login.html

```html
    <body>
        <input type="text" id="username" />
        <input type="password" id="password" />
        <input type="button" id="login" value="登录" />
        <script src="../javascripts/jquery-3.2.1.js"></script>
        <script>
            $(function(){
                $("#login").click(function(){
                    $.ajax({
                        type:"post",
                        data:{
                            username:$("#username").val(),
                            password:$("#password").val()
                        },
                        url:"http://localhost:3000/test/login",
                        async:true,
                        success:function(data){
                            console.log(data);
                        }
                    });
                })
            })
        </script>
```

- test.js

``` js
var express = require('express');
var router = express.Router();
// 注册,配合mysql，连接到数据库，查看账号是否已经被注册
router.post('/register', function(req, res, next) {
    // console.log(req.body);
    var mysql      = require('mysql');
    var connection = mysql.createConnection({
      host     : 'localhost',
      user     : 'root',
      password : '',
      database : 'user'//数据库表格名称
    });
     
    connection.connect();//连接数据库
     
    // 判断用户输入的注册账号是否已经存在于数据库中，即是否已经被注册，若存在，则该注册名不可用，若不存在则将该注册名存入数据库中
    // 使用mysql的连接查询方法connection.query
    // connection.query方法中存在回调函数,所以是异步，用promise解决
    // select * from userdata where ? [{username : req.body.username;}]  表示查看userdata表中的所有数据是否等于req.body.username,若相等，表示已经数据库中存在，则不能使用
    function isExistSameName(){
        return new Promise(function(resolve,reject){
            connection.query('select * from userdata where ? ',[{
                username : req.body.username
                }], function(error, results, fields) {
                  if (error) throw error;
                  console.log(results);
                  if(results.length > 0){//lts.length > 0 表示username有值
                    connection.end();//断开连接
                    res.send('register failed');
                  }else{
                    resolve();
                  }
                });
            });
        }

    // 若用户名未被注册过，则将该用户名插入到数据库中
    function isInsertUser(){
        return new Promise(function(resolve,reject){
            connection.query('INSERT INTO userdata SET ?',[{
                username : req.body.username,
                password : req.body.password
            }],function(error, results, fields){
                if (error) throw error;
                res.send('register success');
                connection.end();
            })         
        })
    } 

        isExistSameName().then(isInsertUser);
  });  

module.exports = router;

```

- app.js

``` js
var loginRouter = require('./routes/test');//备注：表示当前文件夹下的routes目录下的test.js文件
app.use('/test', loginRouter);
```

### 数据操作（参考）

> 来源于二阶段php结合mysql中的数据增删改查操作

- 插入数据

  > 格式：`insert into <表名> [(<字段名1>[,..<字段名n > ])] values ( 值1 )[, (值n )];`

```php
//单条数据
insert into MyGuests (firstname, lastname, email)
values ('John', 'Doe', 'john@example.com')
```

- 删除表数据

  > 格式：delete from 表名 where 表达式

```php
//删除MyGuests表中id为1的数据
DELETE FROM MyGuests where id=1;
//删除所有数据
DELETE FROM MyGuests
```

- 查询表中的数据

  > 格式： select <字段1, 字段2, …> from < 表名 > where < 表达式 >;
  >
  > select一般配合where使用，以查询更精确更复杂的数据。 

```
//查看表 MyGuests 中所有数据
select * from MyGuests;

//查看表 MyGuests 中前10行数据：
select * from MyGuests order by id limit 0,10;
```

- 修改表中的数据。

  > 格式：update 表名 set 字段=新值,… where 条件;

```
update MyGuests set name='Mary' where id=1;
```

## multer

> [参考文档](https://github.com/expressjs/multer/blob/master/doc/README-zh-cn.md)

- express的脚手架之一。

- Multer 是一个 node.js 中间件，用于处理 `multipart/form-data` 类型的表单数据，它主要用于上传文件。它是写在 [busboy](https://github.com/mscdex/busboy) 之上非常高效。
- **注意**: Multer 不会处理任何非 `multipart/form-data` 类型的表单数据。

### 上传文件案例

```html
    <input type="file" id="files" name="uploadFile" multiple/>

    <script type="text/javascript">
        var filesNode = document.getElementById("files");
        // onchange 事件：当你改变输入框内容，离开输入框后，函数将被触发，
        // onchange 事件会在域的内容改变时发生。
        // onchange 事件也可用于单选框与复选框改变后触发的事件。
        // onchange 属性可以使用于： <input>, <select>, 和 <textarea>。
        filesNode.onchange = function(){
            // console.log(filesNode.flies);
            var xhr = new XMLHttpRequest();
            xhr.onreadystatechange = function(){
                if (xhr.readyState == 4 && xhr.status == 200) {
                    console.log(xhr.responseText);
                }
            }
            var data = new FormData();//创建一个空对象实例，可以用append()方法添加数据
            data.append("uploadFile",filesNode.files[0]);
            xhr.open("post","http://localhost:3000/upload/uploads",true);
            xhr.send(data);
            filesNode.value = null;
        }
// 【注意】以上中data.append("uploadFile",filesNode.files[0]);中uploadFile为input标签的name属性值，
    </script>
```

``` js
// 实现上传文件

var express = require('express');
var router = express.Router();
var db = require('../lib/db.js');

// 实现上传必须配置的参数
var multer = require('multer');
// 磁盘存储引擎DiskStorage可以让你控制文件的存储。
var storage = multer.diskStorage({
    // destination 是用来确定上传的文件应该存储在哪个文件夹中。
    destination: function (req, file, cb) {
        cb(null, 'public/my-uploads');//选择储存的文件夹位置，建议先建好文件夹，否则会出现'500'报错
    },
    // filename 给上传的文件重命名。 
    // 如果没有设置 filename，每个文件将设置为一个随机文件名，并且是没有扩展名的
    // 注意: Multer 不会为你添加任何扩展名，但程序应该返回一个完整的文件名。
    // 因此，可以把 abc.jpg图片切割为数组[abc,jpg],然后用数组长度-1来获取后缀名
    // 并且可以给图片加上时间戳格式防止重名名
    filename: function (req, file, cb) {
        var fileFormat = (file.originalname).split('.');
        cb(null, file.fieldname + '-' + Date.now() + '.' + fileFormat[fileFormat.length-1]);
        // console.log(fileFormat[fileFormat.length-1]);
             
    }
})
var upload = multer({ storage: storage });

// .single(fieldname):接受一个以 fieldname（input标签的name属性值） 命名的文件。这个文件的信息保存在 req.file。
router.post('/uploads', upload.single('uploadFile'), function (req, res, next) {
    console.log(res);
    next();
},function (req, res, next){
    res.send('upload success');
});
module.exports = router;
```

### FormData()方法（参考）

> 参考文档自行百度

```html
//通过FormData构造函数创建一个空对象
var formdata = new FormData();
//可以通过append()方法来追加数据
formdata.append("name","laotie");--------------------->name为input标签的name属性值
//通过get方法对值进行读取
console.log(formdata.get("name"));//laotie
//通过set方法对值进行设置
formdata.set("name","laoliu");
console.log(formdata.get("name"));//laoliu
```



# MongoDB

> nosql数据库，不需要sql语句的数据库，里面一切都是类似于JSON文件
>
> [参考文档](https://www.npmjs.com/package/mongodb)
>
> [mongodb教程](https://github.com/Wscats/node-tutorial/issues/20)

- MongoDB 是由C++语言编写的，是一个基于分布式文件存储的开源数据库系统。
- 在高负载的情况下，添加更多的节点，可以保证服务器性能。
- MongoDB 旨在为WEB应用提供可扩展的高性能数据存储解决方案。
- **MongoDB 将数据存储为一个文档，数据结构由键值(key=>value)对组成。MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。**

## 安装

- 双击安装`mongodb.msi`文件
- 找回安装完`mongodb`文件夹`bin`的路径

```
C:\Program Files\MongoDB\Server\3.2\bin
```

里面有多个exe文件

- 在`bin`这个目录下，打开`cmd`命令行，执行以下命令，输入的文件夹路径中若有数据库则连接此数据库，该目录中若没有数据库则执行该命令就是创建数据库成功。

```bash
mongod --dbpath [文件夹的路径](创建的数据的路径)
```

- 安装`robo3t`的可视化软件来管理`mongodb`数据库，没有表的概念，只有集合(类似于mysql的表))
- 配合node来使用`mongodb`数据库,在项目目录下用cmd安装

```bash
npm install mongodb
```

- 新建`server.js`,执行以下代码

``` js
const MongoClient = require('mongodb').MongoClient;
const assert = require('assert');
 
// Connection URL
const url = 'mongodb://localhost:27017';
 
// Database Name
const dbName = '1806';
 
// Use connect method to connect to the server
MongoClient.connect(url, function(err, client) {
  assert.equal(null, err);
  console.log("Connected successfully to server");
  const db = client.db(dbName);
  client.close();
});
```

- 查看数据

``` js
const MongoClient = require('mongodb').MongoClient;
const assert = require('assert');

// Connection URL
const url = 'mongodb://localhost:27017';

// Database Name
const dbName = '1806';

// Use connect method to connect to the server
MongoClient.connect(url, function (err, client) {
  assert.equal(null, err);
  console.log("Connected successfully to server");
  //选择库
  const db = client.db(dbName);
  //选择集合（表）
  db.collection('students').find({//find里的数据若为空，则会查找到所有数据，若有条件，则会找到条件对应的数据
        age: 18
      }).toArray(function (err, docs) {//toArray转成数组
        assert.equal(err, null);
        console.log("Found the following records");
        console.log(docs);//docs为结果
      });
      client.close();
});
```

### robo3t（mongodb可视化操作工具）

操作步骤（参考）：

1. 先要在电脑启动mongoDB，然后打开Robo 3T ，点击“create”创建一个到mongoDB的连接。 
2. 接着在mongoDB启动的情况下，点击connect，Robo 3T 即可连接到mongoDB了。 
3. 在Robo 3T 左上方，可以看到mongoDB里面的数据库了，这就是可视化了。 
4. 在连接上面单击右键，有一个“open shell”，它是用来执行mongoDB中的命令或者语句的。 
5. 此外，你还可以点击Create Database直接新建一个mongoDB的数据库。 
6. 也可以点击Repair Database或Drop Database在数据库上面新建集合 
7. **点击Create connection 创建集合（也就是表）**



## express配合mongodb实现系统的接口

### 案例：后台系统增加查找数据

> 具体查看 C:\Users\Administrator\Desktop\third\05.day5\cms（Content Management System）

### 报错：db.collection is not a function

【注意】在mongodb中db.query返回的是一个函数，所以应该写成：

``` js
db.query(function(db){
        //mongodb中插入数据的操作 
        db.collection('cmsData').insertMany([req.body], function(err, result) {
            console.log("Inserted 1 documents into the collection");
            // 插入完成后才响应
            res.send('respond with a resource');
        });
    })
```



# websocket

WebSocket提供了一个受欢迎的技术，来替代Ajax技术 。HTML5的WebSocket API，它可用于客户端、服务器端。而且有一个优秀的第三方API，名为**Socket.IO** ,这个新的API提供了一个方法，从客户端使用简单的语法有效地推动消息到服务器。 

---

#### ajax

- 前端主动发，后端被动接收（req，res）

#### websocket（作用更广）

- 前端主动发，后端被动接收
- 后端主动发，前端被动接收

##### 安装 `npm install socket.io --save-dev`

---

## Socket.IO

> [socket.io](https://github.com/Wscats/node-tutorial/issues/7)
>
> [npm 参考文档](https://www.npmjs.com/package/socket.io)

---

- **socket.io一部分在node的express下设置**
- **另一部部分浏览器页面下加载`socket.io.client.js`**

#### 在express使用socket

``` js
var app = require('express')();
var server = require('http').createServer(app);
var io = require('socket.io')(server);
io.on('connection', function(){ /* … */ });
server.listen(3000);
```

#### 方法

| 接口            | 描述     |
| --------------- | -------- |
| `socket.on()`   | 发送信息 |
| `socket.emit()` | 接受信息 |

---

## 具体操作案例

> 逻辑：前端发送，后端接收。后端再把接收到的数据发送到前端

### 前端

> **要下载客户端[socket.io.js](https://github.com/socketio/socket.io-client)文件，在页面中引入**

```html
<!DOCTYPE html>
<html lang="en">
</head>
<body>
    <textarea name="" id="massage" ></textarea>
    <input type="button" value="发送" id="send" />
    <ul id="massaegList"></ul>
    <script type="text/javascript" src="../javascripts/socket.io.js"></script>
    <script type="text/javascript" src="../javascripts/jquery-3.2.1.js"></script>
    <script type="text/javascript">
    var socket = io('http://localhost:3001');
            socket.on('connect', function() {});
            socket.on('event', function(data) {});
            socket.on('disconnect', function() {});
            //发送
            $("#send").click(function(){
                socket.emit("sendMsg",$("#massage").val());
            })
		   //接收
            socket.on('getMsg',function(data){
                $("#massaegList").append(`<li>${data}</li>`)
            })
    </script>
</body>
</html>
```

### 后端

> 在express中使用

``` js
// 将socket接口封装再导出到app.js文件中，就可以方便引用
function socket(){
    // In conjunction with Express结合express使用socket
    var app = require('express')();
    var server = require('http').createServer(app);
    var io = require('socket.io')(server);
    io.on('connection', function(socket){ 
        //socket信息的逻辑编写在这里
        //接收
        socket.on('sendMsg',function(data){
            console.log(data);
            //发送
            socket.emit('getMsg',data);
        })
    });
    server.listen(3001);
    //【注意】端口号不可以与其他冲突，如express的端口号为3000，因此这里不要再应用3000端口号
}
// 将接口导出(到app.js)
module.exports = {
    socket
}
```

- app.js中导入socket接口如下：

``` js
//socket路由
require('./routes/socket.js').socket();
```



# Vue

> ##### 渐进式 JavaScript 框架 [vue官网](https://cn.vuejs.org/)
>
> ui插件：mint-ui

- Vue 的核心库只关注视图层  读音view

- 双向数据绑定

  - 选项data里面数据发生变化则视图跟着变化

- Vue与jquery的区别

  - 如果页面注重操作节点，jquery
  - 如果页面数据比较多，建议用vue

- 下载 `vue.js`,并且在HTML文件中引入(`vue.js提供全局变量Vue全局变量`类似于`jquery.js提供全局变量$或者jQuery`)

  ```html
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.17/dist/vue.js"></script>
  ```



## 开发工具vue-devtools

> vue调试开发工具，方便开发Vue项目

- 到github下载vue-devtools

``` bash
git clone https://github.com/vuejs/vue-devtools.git
```

- 在vue-devtools目录下安装依赖包 （看需要安装）

```bash
cd vue-devtools
cnpm install
```

- 修改manifest.json文件 ,把"persistent":false改成true （该步见机行事，若不成功再试试这一步）

``` bash
路径：vue-devtools->shells->chrome->manifest.json
```

![img](https://images2017.cnblogs.com/blog/1055753/201708/1055753-20170827152825605-2132649031.png) 

- 编译代码（该步与上一步同，见机行事，若不成功再试）

``` bash
npm run build
```

- **扩展Chrome插件 **
  - Chrome浏览器 >  更多程序 > 拓展程序 >开发者模式
  - 点击加载已解压程序按钮, 选择 vue-devtools > shells > chrome 放入, 安装成功如下图

![img](https://images2017.cnblogs.com/blog/1055753/201708/1055753-20170827153453605-1374332252.png) 

-  vue-devtools使用
  -  vue项目, 打开f12, 选择vue就可以使用了.
  -  vue是数据驱动的, 这样就能看到对应数据了, 方便我们进行调试
-  温情提示: 

   - vue必须引入开发版, 使用min压缩版是不能使用devtools进行调试的
   - 安装后, 需要关闭浏览器, 再重新打开, 才能使用



## Vue 实例

#### 创建 Vue 实例

> 当引入vue.js之后，创建Vue实例相当于引入jquery后创建 $()实例

``` js
var vm = new Vue({
  // 选项
})

//对比jquery
//jQ，第一要有数据，第二要有节点，没节点，数据没意义
$.ajax()
$(el).html(data)
//寻找节点，然后放数据
```

### ***前言

> 除了数据属性，Vue 实例还暴露了一些有用的实例属性与方法。它们都有前缀 `$`，以便与用户定义的属性区分开来。 

``` js
var data = { a: 1 }
var vm = new Vue({
  el: '#example',
  data: data
})

vm.$data === data // => true
vm.$el === document.getElementById('example') // => true

// $watch 是一个实例方法
vm.$watch('a', function (newValue, oldValue) {
  // 这个回调将在 `vm.a` 改变后调用
})
```



### 实例属性

> Vue 实例里可以放各种**选项、数据、DOM、钩子、资源、组合**，具体参考**[API接口文档](https://cn.vuejs.org/v2/api/)**

- **data**

  - 类型 ： `Object | Function`
  - Vue 实例的数据对象,当数据改变时，视图会重新进行渲染
  - 实例创建之后，可以通过 `vm.$data` 访问原始数据对象。Vue 实例也代理了 data 对象上所有的属性，因此访问 `vm.a` 等价于访问 `vm.$data.a`。 

  ``` js
  var data = { a: 1 }
  
  // 直接创建一个实例
  var vm = new Vue({
    data: data
  })
  vm.a // => 1
  vm.$data === data // => true
  
  // Vue.extend() 中 data 必须是函数
  var Component = Vue.extend({
    data: function () {
      return { a: 1 }
    }
  })
  ```

  - 【例外】使用 `Object.freeze()`，这会阻止修改现有的属性，也意味着响应系统无法再*追踪*变化。 

    ``` js
    var obj = {
      foo: 'bar'
    }
    
    Object.freeze(obj)  //3.当用了Object.freeze(obj)方法后，视图的foo不会被更新，且报错
    
    new Vue({
      el: '#app',
      data: obj
    })
    ```

    ``` html
    <div id="app">
      <p>{{ foo }}</p>   //1.从data拿到数据，页面显示bar
      <!-- 4.这里的 `foo` 不会更新！ -->
      <button v-on:click="foo = 'baz'">Change it</button>  //2.点击使数据变成baz
    </div>
    ```

- **props**

  - 类型 ：` Array<string> | Object `
  - vm.$props

- **el** 

  - 类型 ：`HTMLElement` ，Vue实例使用 的 **根DOM元素**
  - vm.$el

- **options**

  - 类型 ：`object`  ,vm.$options

  - 用于当前 Vue 实例的初始化选项。需要在选项中包含自定义属性时会有用处： 

    ``` js
    new Vue({
      customOption: 'foo',
      created: function () {
        console.log(this.$options.customOption) // => 'foo'
      }
    })
    ```

- **parent**

  - 父实例，如果当前实例有的话
  - vm.$parent

- **root**

  - 当前组件树的根 Vue 实例。如果当前实例没有父实例，此实例将会是其自己。 
  - vm.$root

- **children**

  - 当前实例的直接子组件。**需要注意 $children 并不保证顺序，也不是响应式的。**如果你发现自己正在尝试使用 `$children` 来进行数据绑定，考虑使用一个数组配合 `v-for` 来生成子组件，并且使用 Array 作为真正的来源。 
  - vm.$children

- **slots**

  - 



## vue 接口

>参考**[API接口文档](https://cn.vuejs.org/v2/api/)**



#### 实例化Vue

- 先实例化`Vue`,里面可以放各种**选项、数据、DOM、钩子、资源、组合**，具体参考**[API接口文档](https://cn.vuejs.org/v2/api/)**

```js
var vm = new Vue({
  // 选项
})

//对比jquery
//jQ，第一要有数据，第二要有节点，没节点，数据没意义
$.ajax()
$(el).html(data)
//寻找节点，然后放数据
```

- 在创建的实例对象中，放进必要的选项。**el**和 **data**必须要有。

``` js
var vm = new Vue({
    // 选项
    data:{                //data就是配合使用`{{}}`来渲染数据
        name:"lemon1"
    },
    el:"#demo"    //el就是寻找节点（找作用域）
})
```

``` html
<div id="demo">
    <p>{{num+1+'1'}}</p>   //页面得到  lemon1
</div>
```



#### 选项/数据

- 数据**data**

  - Vue 实例的数据对象。 
  - 实例创建之后，可以通过 `vm.$data` 访问原始数据对象。Vue 实例也代理了 data 对象上所有的属性，因此访问 `vm.a` 等价于访问 `vm.$data.a`。 

  ``` js
  var data = { a: 1 }
  
  // 直接创建一个实例
  var vm = new Vue({
    data: data
  })
  vm.a // => 1
  vm.$data === data // => true
  
  // Vue.extend() 中 data 必须是函数
  var Component = Vue.extend({
    data: function () {
      return { a: 1 }
    }
  })
  ```

  

- 计算属性 **computed**

  - 【注意】定义的属性名不能跟data里面的重复。即data里面已经有的属性，computed里面不能再有该属性
  - 应用：当需要把一个旧数据通过算法转为新数据时
  - 该属性从数据层来改变视图层

  ``` html
  	    <div class="num">
  			<h2 v-text="aComputed"></h2>
  			<h3 v-text="bComputed"></h3>
  		</div>
  ```

  ``` js
  			var vue = new Vue({
  				el : ".num",
  				data : {
  					a : 1,
  					b : 2
  				},
  				computed : {
  					aComputed(){
  						var number = this.a+2
  						return number;
  					},
  					bComputed(){
  						return this.b + 8
  					}
  				}
  			});
  ```

  

- 事件处理器 ****



#### Vue指令

- 文本值 **v-text**   类似于jquery的`$().text();`

``` html
<span v-text="msg"></span>
<!-- 和下面的一样 -->
<span>{{msg}}</span>
```

- 属性值  **v-bind:xxx** 简写为 **：xxx**
- **：style**  和  **：class** 是必须接受一个对象
- **：xxx**  都可以接受任何变量

``` js
//jquery
$().attr();
$().css();
$().addClass();
//vue
<p :name="name"></p>
```

- 插入html结构  **v-html**

``` js
$().html()

<div v-html="html"> </div>
```

- 显示或者隐藏，**v-show**   ，本质是控制css，若节点一直存在的，并且频繁切换的使用该指令（如选项卡、导航条的切换，加载的动画等）

``` js
$().show()
$().hide()

<div v-show="!bool">你好</div>
```

- 对节点增加或者删除，**v-if**    **v-else-if**    **v-else**  节点要么存在或者不存在。（注意与前面的v-show区分使用）

``` js
$().append()
$().remove()

<div v-if="!bool">你好</div>
<div v-else>假的</div>
```

- 遍历 **v-for** 放哪里，那个节点就跟着遍历对应的数组,支持嵌套其他指令`v-for,v-if和v-show`

``` js
$().each()

<div v-for="item in arr" v-text="item.name"></div>
```

- 事件监听 **v-on** ，`v-on:click`简写为`@click`，即将原生的onmousedown->@mousedown，将on改为@，把事件监听函数方法写在选项的`methods`里面。

``` js 
$().on()
$().click()

<button @click="loadMore">查看更多</button>
```

-  **v-model **把视图的值，返回到选项`data`里面。只能在以下三个标签中使用，（自我理解为表单控件）

``` js
<input v-model="name" />  
<select>
<textarea>
//在data中定义了name，那么在视图层输入到表单中的值都会出现在数据层的data的name里面
```





## vue搭建框架流程

> 微博案例

#### 安装脚手架

> https://cli.vuejs.org/

- 全局安装

  ``` bash
  npm install -g @vue/cli      (或者用cnpm安装)
  ```

- 安装完，会在全局有vue命令（版本号）

  ``` bash
  vue -V
  ```

- 创建项目

  ``` bash
  vue create weibo
  ```

- 定位到该文件夹

  ``` bash
  cd weibo
  ```

- 启动服务器

  ``` bash
  npm run serve      (得到一个8080端口)
  ```

#### 组件

- main.js里面的（#app）对应public/index.html 里的id名：

  ``` html
  index.html:    
  <div id="app"></div>
  ```

  ``` js
  main.js:
  new Vue({
    render: h => h(App)  //（我猜是对应App.vue,作为入口文件---有待考证）
  }).$mount('#app')
  //说明是以app开始的，相当于定义了el：app
  ```

- 组件组成部分

  ``` vue
  <!-- html -->
  <template>
    <div id="app">
  		<Xheader />   //其他组件
    </div>
  </template>
  
  <!-- js -->
  <script>
  	// 引入其他的组件
  import Xheader from './components/Xheader.vue';
  import Xlist from './components/Xlist.vue';
  
  export default {
    name: 'app',
    components: {
  		// 其他组件记性注册
      	Xheader,
  		Xlist
    }
  }
  </script>
  
  <!-- css -->
  <style>
  
  </style>
  
  ```

  ```vue
  App.vue/Home.vue(父) = Xheader.vue(子) + Xlist.vue(子)
  ```

  

- **axios** 请求数据

  - 安装 `npm install --save axios `   

  ``` js
  <script>
  	import axios from "axios";
  	export default {
  		data() {
  			
  		},
  		methods:{
  			loadMore(){
  				axios
  					.get("http://localhost:3000/api/getIndex")
  					.then(function(response) {
  						console.log(response);
  					})
  					.catch(function(error) {
  						console.log(error);
  					});
  			}
  		},
  		mounted(){
  			this.loadMore();
  		}
  	}
  </script>
  ```



## Vue-router路由

> 文档  [Vue Router ](https://router.vuejs.org/zh/installation.html)

- 后端是进入各种不同的路径，返回不同的数据
- 前端是进入各种不同的路径，显示不同的页面内容

#### 安装

``` bash 
npm install vue-router --save-dev
```
#### 使用

- 将以下代码写入 main.js 文件里面

  ``` js
  如果在一个模块化工程中使用它，必须要通过 Vue.use() 明确地安装路由功能：
  import Vue from 'vue'
  import VueRouter from 'vue-router'
  
  Vue.use(VueRouter)
  ```

- 定义路由配置参数

  - 如果url的路径为`/home`,在页面显示Home组件(里面包含着子组件)
  - 反之如果路径为`/search`,在页面显示Search组件(里面包含着子组件)

  ``` js
  //写在main.js 里面
  
  // 0. 如果使用模块化机制编程，导入Vue和VueRouter，要调用 Vue.use(VueRouter)
  
  // 1. 定义 (路由) 组件。
  // 可以从其他文件 import 进来
  import Home from "./container/Home.vue";
  import Search from "./container/Search.vue";
  //以下是官方文档的写法-----待学习
  //const Foo = { template: '<div>foo</div>' }
  //const Bar = { template: '<div>bar</div>' }
  
  // 2. 定义路由
  // 每个路由应该映射一个组件。 其中"component" 可以是
  // 通过 Vue.extend() 创建的组件构造器，
  // 或者，只是一个组件配置对象。
  // 我们晚点再讨论嵌套路由。
  const routes = [
    { path: '/home', component: Home },
    { path: '/search', component:Search }
  ]
  
  // 3. 创建 router 实例，然后传 `routes` 配置
  // 你还可以传别的配置参数, 不过先这么简单着吧。
  const router = new VueRouter({
    routes // (缩写) 相当于 routes: routes
  })
  ```

- 把router注入到大容器`new Vue`

  ``` js
  new Vue({
    router,
    render: h => h(App)
  }).$mount('#app')
  // 4. 创建和挂载根实例。(官方写法)
  // 记得要通过 router 配置参数注入路由，
  // 从而让整个应用都有路由功能
  //const app = new Vue({
  //  router
  //}).$mount('#app')
  ```

#### 一级路由

- 写在Ap.vue里

  ``` vue
  <template>
    <div id="app">
  		 <!-- 路由出口 -->
  		<!-- 路由匹配到的组件将渲染在这里 -->
  		<router-view></router-view>
    </div>
  </template>
  ```

- 组件之间的跳转

  ``` vue
  //跳转到search组件页面
   <a href="#/search" class="nav-search unlogin-search">
  //----->跳到http://localhost:8080/#/search
       
  【一开始输入localhost端口时，直接到默认的页面，可以使用路由重定向】
  ```

- 在一开始输入端口号 http://localhost:8080 ，要使页面直接自动跳转到首页的热门页

  ``` js
  //在main.js中
  const routes = [
      // 设置最开始进入端口时呈现的页面(重定向)
      { path: '/',redirect:'/home/hot' }
     ]
  ```

  

#### 嵌套路由(二级路由)

> 案例：微博Home页面

- main.js 中

  ``` js
  // 二级路由
  import HomeChannel from "./container/HomeChannel.vue";
  
  // 2. 定义路由
  // path指向谁，页面就显示哪个组件
  // http://localhost:8080/#/search页面显示Search组建的内容
  const routes = [
  		{ 
  			path: '/home', //----------->一级路由
  			component: Home ,
  			name:'home',//------->给每个路由加上名字
  			children:[  //------->二级路由的设置
  			{
  				path: 'hot',//---------->二级路由
  				component: HomeChannel,
  				name: 'hot'
  			},{
  				path: 'fresh',
  				component: HomeChannel,
  				name: 'fresh'
  			}
  		]
  	},
      
    { path: '/search', name:'search',component:Search },//---->其他一级路由
    { path: '/sign', name:'sign', component:Sign }
  
  ]
  ```

  

- Home.vue中写入

  ``` vue
  <template>
      <div>
          <Xheader status="home" />  <!--头部-->
          
          <!--首页列表部分采用二级路由，-->
          <!--home页面的热门、新鲜事等页面的转化在列表中，因此将热门、新鲜事等页面匹配到的组件渲染到这里-->
          <router-view></router-view>
      </div>
  </template>
  <script>
  import Xheader from "../components/Xheader.vue";
  export default {
    components: {
      Xheader,
    }
  };
  </script>
  ```

- 创建Home的二级路由 HomeChannel.vue

  ``` vue
  <!-- 页面中热门、新鲜事等子页面 -->
  <!-- 基于Home下的二级路由 -->
  <template>
  	<div style="margin-top:84px;">
          <!--Home中的二级路由主要是点击头部的热门、新鲜事等标签进入对应的路由界面（列表页），因此引入列表项-->
  		<Xlist />   
  		<Xlist />
  	</div>
  </template>
  
  <script>
  	import Xlist from "../components/Xlist.vue";
  	export default {
  		data() {
  			return {
  				navs: [{
  						title: "热门",
  						path: "",
  						isSelect: true
  					},{
  						title: "新鲜事",
  						path: "",
  						isSelect: false
  					}
  				],
  				channel: 0
  			};
  		},
  		components: {
  			Xlist
  		},
  		methods: {
  			// 封装二级路由的页面切换，
  			setChannel() {
  				// 判断当前是什么路由
  				// console.log(this.$router.history.current.path);
  				//--------->打印得到/home/hot
  				var route = this.$router.history.current.path;
  				// 在Header.vue页面实现点击selectNav切换路由
  				switch (route) {
  					case "/home/hot":
  						this.channel = 0;
  						break;
  					case "/home/fresh":
  						this.channel = 1;
  						break;
  					default:
  						this.channel = 0;
  				}
  			}
  		},
  		mounted() {   // 进场
  			this.setChannel();
  		},
  		watch: {     //监听
  			$route(){
  				this.setChannel();
  			}
  		}
  		
  	}
  </script>
  
  ```

- 动态的导航到一个新 URL 

  ``` js
  methods: {
      // 选项卡
      selectNav(nav) {
        //二级路由的页面间的切换，（动态的导航到一个新的url）
          //方法一：直接利用路由
          //this.$router.push(`${this.navs[nav].path}`);
          // 方法二：利用二级路由的名字()名字在main.js中设置，更加稳定
          this.$router.push({name:this.navs[nav].path});
      },
  ```

  



## vuex

>组件和组件之间的中介  参考文档 [Vuex](https://vuex.vuejs.org/zh/guide/)

#### 安装

```bash
npm install vuex --save   //这里只用save安装就可以了
```

#### 整体过程

- 组件通过getter从仓库中获取数据

- 组件通过点击事件触发action下达命令，使action触发mutations进行修改数据，最终mutations将数据再次复制给state仓库，完成数据的修改

``` js
//可以形成一个闭环
//组件 -----> actions(下命令) ------> mutations(改) ------> state(仓库) ---->getter(拿) ------>  组件
```

#### 【注意】

- 最好是同一个页面中的组件与组件之间相互通信 ，不同页面之间的组件最好不要用vuex来进行数据传递。
  - 在页面已经改变时，退出的页面生命周期已经结束，此时若两个页面之间的组件利用vuex来传递数据，那么，在刷新页面之后，由于只有一个组件（组件2）和vuex（中介）存在，而退出的页面的个组件（组件1）不存在，此时vuex拿不到组件1中的数据，组件2自然就拿不到vuex仓库里数据。因此该情况容易出现数据丢失的情况。
- 两个页面间数据的传递，可以利用路由来进行传递。
  - 比如将数据放在url上进行传递

#### 使用

- 引入

  ``` js
  //main.js 中引入，调用 Vue.use(Vuex)
  import Vuex from 'vuex'
  Vue.use(Vuex)
  
  
  //创建vuex仓库 Store
  const store = new Vuex.Store({
    //状态
    state: {//----------------------------->中介放数据的仓库
      count: 0,  
      title: "微博",
      author: "lemon",
      description: "这是一个最完美新浪微博客户端"
    },
    //修改状态
    mutations: {
      increment (state) {
        state.count++  // 变更count状态
      }
      editTitle(state, data) {
        state.title = data//-------->从action中拿到data，在复制给state.title，完成修改。此时state里的title数据被修改成data的值
      },
      editAuthor(state, data) {
        state.author = data
      }
    },
    // actions  一般配合 事件@xxx 触发
    actions: {//------------>修改状态提交到mutations
      setTitle(context, data) {
        context.commit('editTitle', data);  //commit表示触发修改状态里的'editTitle'函数，再把data的值赋给editTitle
        context.commit('editAuthor', data)
      }
    },
    //组件从该仓库中获取数据，组件那边配合computed使用
    getters: {
      getTitle: state => {
        return state.title//------------------------>得到title微博
      },
      getAuthor: state => {
        return state.author//------------------------>得到lemon
      },
      getAll: state => {
        return state//------------------------->拿到state里的所有数据
      }
    }
  })
  
  
  new Vue({
      router,//------------------------->注入路由功能
      store，//------------------------->注入仓库功能
  	render : h=>h(App)    
  }).$mount('#app')
  ```

  

- 组件从veux仓库中获取数据，配合 computed

  ``` js
  computed: {
      navs() {
        return this.$store.getters.getNavs;
      },
      nav: {
        // getter
        get: function() {
          return this.$store.getters.getNav;
        },
        // setter
        set: function(newValue) {
          this.$store.state.nav = newValue;//把更改的路由数据赋值给vuex仓库里的nav（个人理解）
        }
      }
  ```

- 组件将数据传递给仓库进行修改等工作

  ``` js
  //Action 通过 store.dispatch 方法触发
  methods: {
      // 切换Xbox
      toggleXbox() {//---------->toggleXbox为点击事件
        this.$store.dispatch("setTitle", "微信");
        //---->通过 store.dispatch 方法触发将"微信"赋给仓库中的actions中的setTitle中的data。(最终将state中的title变成"微信")
      }
    }
  ```

- 应用

  - 在vue中组件都是独立的。

  - 若两个组件之间的数据相同，或想改的数据相同，此时可以利用veux作为中介仓库，组件1将改变的数据存入仓库，组件2就可以直接从仓库获取数据。从而达到组件之间相互独立但有能有联系的功能。

  - 再次说明，vuex相当于组件之间存储数据的仓库。

  - 具体案例：如微博中的导航条和隐藏导航条，两个导航条触发的数据要一样，如下图，当导航条中切换到搞笑，隐藏导航条同样需要切换到搞笑，此时就可以利用vuex进行数据的传递。

    ![vuex案例示意图](C:\Users\Administrator\Desktop\third\vuex案例示意图.png)

  - （个人理解）当两个组件要通过vuex联系时，两个组件中都使用同一套代码，如案例中，两个组件都要用到以下代码

  ``` js
    computed: {
      navs() {
        return this.$store.getters.getNavs;//------>1.1从vue仓库中获取到getNavs数据
      },
      nav: {
        // getter
        get: function() {
          return this.$store.getters.getNav;//--------->2.1从vuex仓库中获取到getNav，
        },
        // setter
        set: function(newValue) {
          this.$store.state.nav = newValue;//--------->2.2将修改的值赋给原来的，即改变原来的值
        }
      }
    },
    methods: {
      // 选项卡
      selectNav(nav) {
        //this.nav = nav;
        //this.$router.push(`${this.navs[nav].path}`);
        this.$router.push({ name: this.navs[nav].path });//--->1.2利用路由名字，使用push方法动态的导航到一个新 URL，（具体为点击对应的navs[nav]，即点击到热门进入热门页面对应的路由）
        this.$store.dispatch("setNav", nav);//--------->2.3利用dispatch发送给vue仓库，修改仓库中的值
      },
      setChannel
    },
    mounted() {
      this.setChannel("nav");  //setChannel为外部封装的数据，【判断当前是什么路由】如下表
    }
  ```

  ``` js
  function setChannel(type) {
      //判断当前是什么路由
      var route = this.$router.history.current.path;
      switch (route) {
          case "/home/hot":
              this[type] = 0;
              break;
          case "/home/fresh":
              this[type] = 1;
              break;
          default:
              this[type] = 0;
      }
  }
  export default setChannel
  ```

  



### Vue项目

> 马蜂窝       蚂蚁短租     





# react

> [中文文档](https://react.docschina.org/)
>
> UI插件：framework     amaze ui   ant Design  weui  material-ui.com

- **虚拟DOM**   jQuery是全局更新DOM，react是局部更新DOM ，尽量减少对DOM的操作
- react：性能的优化

## 安装

- git下载安装包

  ```
  https://github.com/facebook/create-react-app
  ```

- 全局安装该模块

  ``` bash
  https://github.com/facebook/create-react-app
  ```

- 安装完毕后会在全局有一个命令 `create-react-app`

- 使用 `create-react-app`初始化项目

  ``` bash
  create-react-app [xxx项目名称]
  ```



### react-devtools

> 安装扩展程序  , 或者用[该包](C:\Users\Administrator\Desktop\third\react\react-developer-tools)

- 下载安装包

``` bash
git clone https://github.com/facebook/react-devtools.git
```

- node build，如果缺少`chalk`,安装chalk后再次node bulid

``` bash
cnpm install chalk

node bulid
```

- 下载回来，进入`react-devtools`文件夹，然后安装依赖
- 在进入`shells/chrome`里面执行`node build`
- 在chrome浏览器打开`chrome://extensions/`，打开开发者模式
- 加载`shells/chrome/unpack`目录，安装插件成功



##  组件

> react定义组件，先创建xxx.js文件，再在文件中引入react模块

- 在文件中引入react模块

  ``` js
  import React, { Component } from 'react'; //每一个js文件都要先引入react
  
  import logo from './logo.svg';//引入图片
  import './App.css';  //引入css文件
  ```

- 所有组件继承于Component

  ``` js
  class App extends Component {//APP.js文件继承于Component
    render() {  //渲染页面
      return (
        <div className="App">  //className相当于class
          <header className="App-header">
            <img src={logo} className="App-logo" alt="logo" />
          </header>
        </div>
      );
    }
  }
  ```

- 导出组件

  ``` js
  export default App;   //导出
  ```



## react实行单项数据绑定

### 数据

model

```
this.state = {
    name:"ly"
}
```

view

```
<p>{this.state.name}
```



### 事件

vue->@click

```
onChnage={}
onClick={}
onKey={}
```



## react-router-dom 路由 

> [参考文档](https://reacttraining.com/react-router/web/example/basic)



## JSX

> JSX是一种JavaScript的语法扩展。
>
> 我们可以在JSX当中任意使用JavaScript表达式，在JSX当中的表达式要包含在大括号中

``` jsx
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
);
```



## react-redux

> Redux 是 JavaScript 状态容器，提供可预测化的状态管理。
>
>  [参考文档](https://www.redux.org.cn/)      [githu参考文件](https://github.com/Wscats/react-tutorial/issues/8)

### 安装

在项目目录下安装以下模块

``` bash
npm install --save react-redux
npm install --save redux
```



### 引入

在App.jsx 或index.js 文件中引入

``` js
//redux
import {Provider, connect} from 'react-redux';
import {createStore} from 'redux';
```



### 配置Action

> 要更新state数据时，需要发起一个action请求，用action来描述所有变化。

``` js
// Action  用来描述所有的变化
const increaseAction = {
  type: 'increase'
}

const multiAction = {
  type: 'multi'
}
```



### 配置Reduce（仓库即store里的counter）

> 为了把action和stat串起来，开发一些函数，即reducer利用action管理整个应用的state 
>
> 灵活运用`...`运算符或者`Object.assign()` 

- 用`...`运算符表示继承了什么什么，如 `...state`表示继承了state（大概这个意思）

- Object.assign()方法用于将所有可枚举的属性的值从一个或多个源对象复制到目标对象。它将返回目标对象 

- 谨记永远不要修改state，而是返回一个全新的state 

  ``` js
  // Reducer  
  function counter(state = {
    count: 0
  }, action) {
    const count = state.count
    switch (action.type) {
      case 'increase':
        return {
          ...state,
          count: count + 2
        }
      case 'multi':
        return Object.assign({}, state, {name: action.name});
      default:
        return state
    }
  }
  ```



### 创建store

``` js
// Store  创建仓库
const store = createStore(counter);
```



### 将创建store和reducer结合

``` js
// Reducer  创建仓库
const store = createStore(function(state={
    
	// 定义isShowActionSheet的初始状态，其他控制isShowActionSheet的都是改变这里的isShowActionSheet
	isShowActionSheet:false

}, action){
	const count = state.count
	switch (action.type) {
		case 'increase':
			return {
				...state,
				count: count + 2
			}
		case 'multi':
			return Object.assign({}, state, { name: action.name });
		case 'toggleSheet' :  //toggleSheet为案例中的点击事件，理解：action的类型，也就是用于更新state的方法
			return {
				...state,   //表示继承了state，这样下面的数据改变才有效果
				isShowActionSheet:action.isShowActionSheet
			}
		default:
			return state
	}
})
```



### Provider

> react-redux 提供的一个 React 组件 ,把 store 提供给其子组件 

- 在原应用组件上包裹一层，使原来整个应用成为Provider的子组件

- 接收Redux的store作为props，通过context对象传递给子孙组件上的connect (**context 有待研究**)

  ``` js
  {/*index.js中*/}
  ReactDOM.render(
  	<Provider store={store}>
  		<Router>
  			<div>
  				<Route path="/home/" component={Home} />
  				<Route path="/detail/" component={Detail} />
  				<XactionSheet />
  				{/* 重定向【设置默认路由】 */}
  				<Redirect path="/" to={{ pathname: '/home/wechat' }} />
  			</div>
  		</Router>
  	</Provider>,
  
  	document.getElementById('root')
  );
  
  ```

#### 网络参考

> [地址](https://www.jianshu.com/p/ef6269d9d75a)

**核心代码**

``` js
export default class Provider extends Component {
  getChildContext() {
    return { store: this.store }
  }

  constructor(props, context) {
    super(props, context)
    this.store = props.store
  }

  render() {
    return Children.only(this.props.children)
  }
}

if (process.env.NODE_ENV !== 'production') {
  Provider.prototype.componentWillReceiveProps = function (nextProps) {
    const { store } = this
    const { store: nextStore } = nextProps

    if (store !== nextStore) {
      warnAboutReceivingStore()
    }
  }
}

Provider.propTypes = {
  store: storeShape.isRequired,
  children: PropTypes.element.isRequired
}
Provider.childContextTypes = {
  store: storeShape.isRequired
}
```

- 首先，对原组件进行了封装： **render方法中, 渲染了其子级元素, 使整个应用成为Provider的子组件。**

  （1）this.props.childern用于获取当前组件的所有子组件
   （2）Children为react内部定义的顶级对象, 该对象封装了一些方便操作字组件的方法. Children.only用于获取仅有的一个子组件,没有或者超过一个均会报错. 所以注意: 确保Provider组件的直接子级为单个封闭元素，切勿多个组件平行放置

- 其次，传递store
   （1）constructor方法: Provider初始化时, 获取到props中的store对象;
   （2）  getChildContext方法: 将外部的store对象放入context对象中，使子孙组件上的connect可以直接访问到context对象中的store。

注：    context可以使子孙组件直接获取父级组件中的数据或方法，而无需一层一层通过props向下传递。context对象相当于一个独立的空间，父组件通过getChildContext()向该空间内写值；定义了contextTypes验证的子孙组件可以通过this.context.xxx，从context对象中读取xxx字段的值。

 

 ### 配置Connect（Connect在案例中的使用）

首先在需要连接的组件中引入以下代码

``` js
//作用：连接React组件与 Redux store
import { connect } from 'react-redux';
```
使用connect连接

``` js
export default connect((state) => {
	return state
},(dispatch) => {
	return {
		toggleSheet() {
			// console.log(ActionSheet is show);
			dispatch({
				type: "toggleSheet",
				isShowActionSheet: true,
			}) 
		}
	}
})(Xheader);
```



### 配置Connect（参考git文档）

> 作用：连接React组件与 Redux store 

```
connect([mapStateToProps], [mapDispatchToProps], [mergeProps],[options])

```

#### mapStateToProps

> 这个函数允许我们将store中的数据作为props绑定到组件上

1. 这个函数的第一个参数就是 Redux 的 store，你不必将 state 中的数据原封不动地传入组件，可以根据 state 中的数据，动态地输出组件需要的（最小）属性，也就是说我们可以按需返回我们需要的store数据
2. 函数的第二个参数 ownProps，是组件自己的 props，有的时候，ownProps也会对其产生影响。

当 state 变化，或者 ownProps 变化的时候，mapStateToProps 都会被调用，计算出一个新的 stateProps，（在与 ownProps merge 后）更新给组件

```
mapStateToProps(state, ownProps)

```

#### mapDispatchToProps

> connect 的第二个参数是 mapDispatchToProps，它的功能是，将action作为props绑定到组件上

```
mapDispatchToProps(dispatch, ownProps)

```

#### [mergeProps],[options]

不管是 stateProps还是dispatchProps，都需要和ownProps合并之后才会被赋给组件，所以组件既有**state数据**也有**action方法**，connect 的第三个参数就是用来做这件事。通常情况下，你可以不传这个参数，connect 就会使用Object.assign替代该方法

`[options] (Object) `如果指定这个参数，可以定制 connector 的行为。一般不用



#  论constructor( )和super( )

## constructor( )构造方法

>  这是ES6对类的默认方法，通过 new 命令生成对象实例时自动调用该方法。并且，该方法是类中必须有的，如果没有显示定义，则会默认添加空的constructor( )方法。

## super( ) 继承

- 在class方法中，继承是使用 extends 关键字来实现的。子类 必须 在 constructor( )调用 super( )方法，否则新建实例时会报错。
- 报错的原因是：子类是没有自己的 this 对象的，它只能继承自父类的 this 对象，然后对其进行加工，而super( )就是将父类中的this对象继承给子类的。没有 super，子类就得不到 this 对象。



## Es5与Es6关于继承的实现不同之处

> 出现上面情况的原因是，ES5的继承机制与ES6完全不同。

### 复习——ES5中new

- 当一个构造函数前加上new的时候，背地里来做了四件事：
  - 生成一个空的对象并将其作为 this；
  - 将空对象的 __proto__ 指向构造函数的 prototype；
  - 运行该构造函数；
  - 如果构造函数没有 return 或者 return 一个返回 this 值是基本类型，则返回this；如果 return 一个引用类型，则返回这个引用类型。
- 简单解释，就是在ES5的继承中，先创建子类的实例对象this，然后再将父类的方法添加到this上（ Parent.apply(this) ）。而ES6采用的是先创建父类的实例this（故要先调用 super( )方法），完后再用子类的构造函数修改this。



### super(props)---super()---以及不写super的区别

- 如果你用到了constructor就必须写super(),是用来初始化this的，可以绑定事件到this上;
- 如果你在constructor中要使用this.props,就必须给super加参数：super(props)；
- **（无论有没有constructor，在render中this.props都是可以使用的，这是React自动附带的；）**
- **如果没用到constructor,是可以不写的；React会默认添加一个空的constructor。**
- **如果在render函数以外要使用this，就调用super()方法 **



## 项目

#### 路由重定向

> [百度](https://blog.csdn.net/wangrong111222/article/details/80720981)

- 在所有组件路由最后添加 `<Redirect exact path="/" to={{ pathname: '/home/' }} /> `作用就是 进入页面 直接进入到Redirect  to的那个位置 ；就是一个强制跳转 
- 但是报错：“You tried to redirect to the same route you're currently on: "/home"” ,
- 在所有组件路由前加 `<Route path="/" render={() => (<Redirect to="/home"/>)}></Route > `还报错（百度）
- 最后选择直接在 home路由用`path="/"`,地址 `localhost:3000/#/`(试了在外层套<Switch>,结果一样的)
- 其他组件地址 `localhost:3000/#/CourseList`

#### input的value为空警告？

- input标签有空的value=“ ”

Warning: Failed prop type: You provided a `value` prop to a form field without an `onChange` handler. This will render a read-only field. If the field should be mutable use `defaultValue`. Otherwise, set either `onChange` or `readOnly`.

警告：prop类型失败：在没有onChange处理程序的情况下，您向表单字段提供了值prop。这将呈现只读字段。如果字段应该是可变的，请使用Debug值。否则，设置Onchange或Read OnLead。



#### React单个文件中定义多个组件

> 若需要将多个组件放在 `common.js` 文件中

- 在 `common.js` 定义

``` jsx
class SelectCity extends React.Component{};
class SelectProduct extends React.Component{};
```

- 在 `common.js` 导出

  ``` jsx
  export { SelectCity， SelectProduct}
  ```

- 在其他文件需要用到 `common.js` 的组件时，导入

  ``` jsx
  import { SelectCity,SelectProduct} from 'common.js'
  ```



#### 方法没有执行而产生的警告

```Consle
Warning: Functions are not valid as a React child. This may happen if you return a Component instead of <Component /> from render. Or maybe you meant to call this function rather than return it.
```

解决：在render中问了使用页面二级跳转，使用了({})方法将最后一个return包裹，，可是最后没有执行该方法，导致警告。所以只要在该方法背后自执行下(后面加个括号)就好啦。



#### history

> 关于history   npm中有文档，react文档中也有。另外查找的  [百度文档链接](https://segmentfault.com/a/1190000010251949)

在有搜索栏的头部，点击搜索到搜索页面，点击搜索页面的取消返回前一页。一开始想到history.goBack方法。经过各种查找啊啊啊啊啊，嗯嗯，如下

- 首先安装history

  ``` bash
  cnpm install --save history
  ```

- 在页面引入（这里的只是引入`createBrowserHistory`）

  ``` jsx
  import { createBrowserHistory } from "history";
  ```

- 将`createBrowserHistory()`方法赋给history

  ``` jsx
  const history = createBrowserHistory();
  console.log(history);//------------------>里面有location，以及很多方法
  ```

- 打印history，得到很多东西，以下为本次用到的

  ```js
  goBack
  location：{hash: "#/Search"，pathname: "/"，……}
  ```

- 两个思路：

  - 最初，想要获取到hash值，然后用link to 跳转，但出现各种问题，比如跳着跳着路由乱了，最后通过截取数组等，终于也能正常 link to。但是！前面一页若没有刷新，则跳转的都是有刷新过的页面，但是用路由跳转的页面不会刷新，因此……失败。
  -  然后！我想到用GoBack方法，，之前不用是因为不懂用link to 该怎么使用，于是！在a标签中使用 onClick 事件！嗯嗯嗯，直接 `onClick={history.goBack} ` . 大功告成！



#### 关于this.setState is not a function 的报错解

1. 有可能是this指向错误，改用箭头函数。

2. [百度] 解决方式就是： 1、使用ES6 箭头函数。 2、不使用箭头函数，在函数结尾 .bind(this) 




#### 使用事件监听时，要记得移除监听

> 我在两个页面中都使用了监听滚动，出现警告 如下：

``` 
Can't perform a React state update on an unmounted component. This is a no-op, but it indicates a memory leak in your application. To fix, cancel all subscriptions and asynchronous tasks in the componentWillUnmount method.
无法对卸载的组件执行响应状态更新。这是一个no-op，但它表示应用程序中存在内存泄漏。要修复，请在componentWillUnmount方法中取消所有订阅和异步任务。
```

> 以及在某个页面中报错表示找不到另一个页面的监听事件定义的事件。

嗯嗯嗯嗯！然后加上componentWillUnmount移除监听事件就好了……

``` jsx
    componentDidMount() {
        // 挂载页面滚动监听
        window.addEventListener('scroll', this.bindScroll,true)//虽然我做的时候没有加true
    } 
    componentWillUnmount() {
            // 移除页面滚动监听
            window.removeEventListener('scroll', this.handleScroll);
        }
```



#### 在监听事件中可以触发函数

``` jsx
  componentDidMount() {
    window.addEventListener('scroll', this.handlesScroll);
  }
  componentWillUnmount() {
    // 移除页面滚动监听
    window.removeEventListener('scroll', this.handlesScroll);
  }

  handlesScroll = () => {
      this.props.ListScroll()   //---->触发reducer中的ListScroll函数
  }
```



#### 关于React页面跳转后新页面不能回到顶部的问题 

> 在 React 组件间进行页面跳转后，发现页面的位置并不在页面顶部，而是在页面跳转前的位置。就是说浏览器的滚动条并没有回到顶部的位置。 

解决方法

``` jsx
//方法一：（可能是ref那一块没有设置好，该方法没有成功）
class MyComponent extends Component {
  componentDidMount() {
    this.node.scrollIntoView();
  }
  render() {
    return <div ref={node => this.node = node} />
  }
}

//方法二：强行（成功，在该项目中，在头部组件中使用，则重新进入每一个页面时，都会回到顶部，
//单独在某个页面的组件中使用，则只有使用的页面才会回到顶部）
componentWillMount(){
    document.getElementById('root').scrollIntoView(true);//为ture返回顶部，false为底部
}
```

##### scrollIntoView

``` jsx
Element.scrollIntoView() 方法让当前的元素滚动到浏览器窗口的可视区域内。

【注意】取决于其它元素的布局情况，此元素可能不会完全滚动到顶端或底端

【详情再百度吧！】
```





#### 关于react页面之间传参的方式

> 本次项目中使用到的方法

##### redux传参

- 【注意】利用redux在不同页面传参时，当接收参数的页面刷新后，参数会消失（根据redux传递的id作为主键渲染页面，刷新后接收到的id也被刷新，因此接收不到参数即参数消失）

- 利用redux创建reducer仓库，（实际上两个页面都从数据中获取参数）。【注意判断弹窗的index是否与点击的头像的index相同，是的话，就在弹窗组件渲染第index个数据】

  - 头像组件：

  ``` jsx
  //利用redux，实现点击哪个头像，就出现弹窗，弹窗中的头像与名字信息与点击的同
  
  //头像页面：render中的内容
  <ul className="teacher-list">
      {(() => {
          return this.props.teachersData.map((item, index) => {
              return (
                  <li key={index} data-index="0">
                      <img onClick={this.props.toggloTeacherPop.bind(this, index)} className="teacher-avatar" src={item.avatar} alt="" />
                      <p className="teacher-name">{item.teacherName}</p>
                  </li>
              );
          });
      })()}
  </ul>
  
  //连接仓库
  export default connect((state) => {
      return state
  }, (dispatch) => {
      return {
          toggloTeacherPop(index) {
              console.log(this.props.teachersData[index]);
              dispatch({
                  type: "toggloTeacherPop",
                  isTeachersPop: true,  //------点击弹窗
                  teacherIdx: index   //--------点击到哪个，就将哪个的index传递到数据库，改变teacherIdx，
              });
          },
      }
  })(XIntroduceTeacher);
  
  ```

  - 仓库页面 index.js

  ``` jsx
  // Reducer  创建仓库
  const store = createStore(function (state = {
      teacherIdx: 0,     
      teachersData: [
              {   
                  avatar: 'http://f2.c.hjfile.cn/pic/201505/470cee05-dc4e-4def-93a7-ef34bfff6b0a_n.png',
                  teacherName: '小兜老师',
                  summary: '沪江网校教师，主授四六级系列课程。对四六级考试有多年研究经验，就四六级词汇更有个人独到的看法。语言功底扎实，授课平实且风趣幽默，深受学生喜爱。'
              }，
          ……
        ]
     }, action) {
        case 'toggloTeacherPop' :
          return {
              ...state,
              isTeachersPop: action.isTeachersPop,
              teacherIdx: action.teacherIdx
          }
  ```

  - 弹窗组件

  ``` jsx
  {(() => {
      return this.props.teachersData.map((item, index) => {
          if(index == this.props.teacherIdx){    
              //------------->【判断index是否与teacherIdx，即判断当前的index是否与点击的头像的index相同，是的话，就在弹窗组件渲染第index个数据】
              return (
                  <div key={index} className="content">
                      <img src={item.avatar} className="img" />
                      <div className="hi"></div>
                      <div className="text">
                          <div className="name">
                              {item.teacherName}
                          </div>
                          <div className="desc">
                              {item.summary}
                          </div>
                      </div>
                  </div>
              );
          }
      });
  })()}
  ```



##### router传参

- 利用Link to 传参

  - 列表页，数据也是从reducer仓库中获取

  ``` jsx
  return this.props.courseData.map((item, index) => {
      return (
          <Link  key={index} to={`/detail/${item.dataId}`} className="ke_info" data-classid={item.dataId} >
              <span className="tit">{item.title}</span>
              <span className="ori_price">￥{item.ori_price}{item.small_ori_price}</span>
              <span className="desc">{item.desc}  {item.time}</span>
          </Link>
      );
  });
  ```

  - 详情页    
    - {路由跳转成功，得到 `http://localhost:3000/#/detail/18390647`},但是组件中打印props为空
    - 解决方法请看下一点【注意】内容

  ``` jsx
  {/*一开始没有成功
  （原因：跳转到详情后，containers\Detail\DetailCourse\DetailCourse.jsx中路由重定向最初为detail/XdetailHome,因此把数据接在了detail/后面，没有传递成功）
  【解决】：containers\Detail\DetailCourse\DetailCourse.jsx中路由改为 /detail/:dataId
  */}
  render() {
      return (
          <div className="tab-content">
              <div className="tab-content-item tab-basic-info">
                  <Router>
                      <Switch>
                          <Route exact path="/detail/:dataId" component={XdetailHome}/>
                          <Redirect path="/" to={{ pathname: '/detail/:dataId' }} />
                      </Switch>
                  </Router>
              </div>
          </div>
      );
  }
  ```

  

- 【注意】用Link传递的数据，接收的页面需要先从最大的组件开始接收，然后一层一层传递到需要使用的组件中

  ``` jsx
  class Detail extends Component {
    constructor(props) {
      super(props);      // -------->得到props
      this.props = props;
      // console.log(this.props.location.pathname);
    }
    render() {
      return (
        <div>
          <Xheader />
          <XPlayer />
          <XdetailNav />
          <DetailCourse url={this.props.location.pathname}/>  {/*--->将props传递给子组件*/}
          <XdetailFooter />
        </div>
  
      );
    }
  }
  ```

  
