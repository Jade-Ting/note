# 二、JavaScript

### *❶js历史

​	1、JavaScript出现于1995年，由Netscape网景公司程序员 Brandan Eich 布兰登与与sun公司联合开发，最初叫Mocha，后被网景公司改为LiveScript。后网景公司与sun公司（Java语言的发明者）达成协议，叫JavaScript，网景公司可以借助Java语言的声势。

​	2、注意：不存在ECMAScript 4.0版本。

​	3、2015年6月，ECMAScript 6正式发布，并且更名为“ECMAScript 2015”。

### *❷注意事项

#### 	（一）找bug

​			1、console    提示bug

​			2、soure    打开对应的js代码→打开watch→在watch里面添加需要观察的变量→f5刷新→按f11跳到下一步→按f10跳过这段函数（不看其中某段函数）。

#### 	（二）window.onload = function(){}

​			当页面中的所有内容(body中的内容)加载完毕后，才执行函数里面的代码。用来在head中写js代码。

#### 	（三）拼接

​			" + 元素+  "

​			若想在输出多个值作为元素的内容，可以考虑字符串拼接的方式。在循环结束后，再给元素赋值。

## 一、js基础

###  一、js语法

#### 	（一）js的书写位置 

​        	1.script[src引入外部js文件][type="text/javascript"可以省略]
      			若是存在src属性，在当前script标签里写代码无效。
      		2.作为a标签的href属性值[href="javascript:js代码;"]

####          （二）js注释

​            	//单行注释
           	 /*多行注释,不要嵌套多行注释*/

#### 	（三） 声明变量及赋值

​        	1. 声明变量(容器)，通过关键字 var
        		var a;
        	2. 给变量赋值,将10的值赋给a
        		a = 10;
        	3. 同时声明变量及赋值  var 变量名 = 值;
       			 var uname = "lemon";
        	4. 同时声明多个变量，用逗号隔开
      			 var b,c,d;
     			 b = 100;
      			 c = 200;
     			 d = 300;
       			  var b = 100,c = 200,d = 300;

### 二、数据类型（值）

####         （一）基本数据类型

#####         	1、数字类型 Number

​        		var uage = 17;

#####         	2、字符串类型String

​			带引号的值都是字符串类型
      		 	 var uname = "lemon"; 

#####         	3、布尔类型 Boolean

​			两个值：true、false
       			 var result = true;

#####     		4、字符串引号嵌套引号 

​    			备注：报错SyntaxError 语法错误 
    			（1）将外层引号改成不一样的（单引、双引）
    			（2）通过反斜杠\转义字符
   				 var sayHi = "Hello,my name's Lily.";
   				 var sayHi = 'Hello,my name\'s Lily.';

#### 	（二）特殊数据类型

#####         		1、Null 类型

​				只有一个特殊的值为 null,表示一个空对象引用(指针)。
        			var num1 = document.getElementById("num1");
       				 console.log(typeof(num1));

#####         		2、Undefined 类型

​				只有一个值undefined。当声明一个变量但未赋值，返回undefined。
       				var uname;
        			 console.log(uname);
        			备注：区分undefined与not defined
        					undefined 声明变量未赋值
        					not defined 报错，变量未声明定义

####         （三） 引用数据类型

​        			Array、Object

#### 	（四）typeof() 判断数据类型

```
				typeof(123);//number
       			typeof(NaN);//number
        		typeof("123");//string
       			typeof(true);//boolean
      		  	typeof(null);//object 
       			typeof(undefined);//undefined
```

### 三、输出 

#####         	1、alert(变量不加引号||具体的值) 弹窗输出

​        	alert(uname);
        	alert(10);
        	alert("uname");

#####         	2、document.write(变量不加引号||具体的值) 

​		在body里面输出内容

​		document.write() 可配合标签使用
		document.write("啦啦啦，我是买包小行家<br/>");

​    		document.write("不问天明去买包<br />");
    		document.write(uname);
    		document.write('<div>我的名字叫'+uname+'</div>')
    		document.write('<div style="color:'+color+';">我的名字叫'+uname+'</div>');

#####     		3、console.log(变量不加引号||具体的值) 

​		往控制台console输出内容

​    		调试
       		console.log(uname);
   		console.log(true);

​    // ??如何进行变量及字符串拼接（见算术运算一）

### 四、运算

####        （一）算术运算 + - * / %(求余数)

​        	1.字符串拼接： 当+运算符两侧有一侧为字符串，此时为字符串拼接。例如1+"2"="12".
        		备注：字符串内拼接变量口诀 "+变量+" (引号可以是单引号)

#####  		例题：计算两个文本框算术运算？

###### 			1、步骤：

​			1.获取到两个文本框 document.getElementById("id名")
        		2.获取到两个文本框里面的内容 value
        		3.文本框内容进行算术运算，将最终结果输出。
        		4.点击按钮时，才执行23代码
        			（1）给按钮元素添加点击事件 [onclick="函数名()"]
        			（2）定义函数，函数里面定义23代码 function 函数名(){js代码}

###### 			2、备注遇到的问题（点击事件）：

​        		（1）代码执行顺序是从上往下的，必须在元素创建之后才能获取
        		（2）点击事件[onclick="函数名()"]触发函数,自定义函数通过function 函数名(){js代码}
        		（3）文本框的值肯定是字符串类型，会存在字符串拼接的问题

```
<body>
    <input type="text" id="num1" />
    <input type="button" value="+" onclick="jia()"/>
    <input type="button" value="-" onclick="jian()"/>
    <input type="text" id="num2" />
    <script type="text/javascript">
        var num1 = document.getElementById("num1");
        var num2 = document.getElementById("num2");
        function jia(){
            var _num1 = num1.value;
            var _num2 = num2.value;
            var jieguo = Number(_num1) + Number(_num2);
            console.log(jieguo);
        }
         function jian(){
            var _num1 = num1.value;
            var _num2 = num2.value;
            var jieguo = _num1 - _num2;
            console.log(jieguo);
        }    
    </script>
</body>
```

###### 	3、补充：点击事件执行函数

```
<body>
    <input type="number" id="num1" />
    <input type="number" id="num2" />
    <input type="button"  value="比较大小" id="btn" />
    <script type="text/javascript">
        //1.获取文本框及按钮
        //2.点击按钮,函数｛
        //  2.1 获取两个文本框的值
        //  2.2 分支判断
        //  2.3 输出到按钮里面
        //｝
        var num1 = document.getElementById("num1");
        var num2 = document.getElementById("num2");
        var btn = document.getElementById("btn");
        // function compare(){
        //     var _num1 = Number(num1.value);
        //     var _num2 = Number(num2.value);
        //     if(_num1>_num2){
        //         btn.value = "用户1获胜";
        //     }else if(_num1 < _num2){
        //         btn.value = "用户2获胜";
        //     }else{
        //         btn.value = "平局";
        //     }
        // }
        // btn.onclick = compare;
        
        btn.onclick = function(){
            var _num1 = Number(num1.value);
            var _num2 = Number(num2.value);
            if(_num1>_num2){
                btn.value = "用户1获胜";
            }else if(_num1 < _num2){
                btn.value = "用户2获胜";
            }else{
                btn.value = "平局";
            }
        }
        // 补充：
        //  点击事件执行函数
        //  1.（1）给元素添加[onclick = "函数名（）"]   （2）定义函数：function 函数名(){}
        //  2. (2) ele.onclick = 函数名  （2）定义函数：function 函数名(){}
        //  3. ele.onclick = function(){}   <== 匿名函数
    </script>
</body>
```



#### （二）赋值运算

​        	1. =  将右边的值赋值给左边  
        	2. += 在原来基础的内容上追加内容
        	3. 同理 -=    *=    /=   %=

#### （三）关系运算

​		返回布尔值(存在隐式转换)

​        		1、 == 等于，判断两边的值的内容发生隐式转换后一致，就返回true
        		2.、!= 不等于，只有当两边的值的内容发生隐式转换后不一致，才返回true
        		3、>  >=  <  <=
        		4、 === 全等于，只有类型以及内容都一致的情况下（不发生隐式转换），才会返回true
        		5、!==  不全等于
        		6、关系运算符的比较规则: 
        			1. 数字和数字比较, 直接比较大小
        			2. 数字和字符串比较, 字符串转换为数字后再比较
        			3. 字符串和字符串比较, 进行字符的ASCII码值比较

### 五、数据类型的转换

####         （一）直接转换

​        	（1）Number() 转换成数字类型
        			Number(字符串) => 数字、NaN
     				Number(布尔值) => 1、0
       				 console.log(Number("123")); //123
       				 console.log(Number("abc")); //NaN(非数字),属于数字类型的一个特殊值。
        			console.log(Number(true));  //1
       				console.log(Number(false));  //0
        	（2）String() 转换成字符串类型,在值两侧加双引号
       				 console.log(String(123));//"123"
       				 console.log(String(true));//"true"
        	（3）Boolean() 转换成布尔类型,true、false
        			备注：数字0、NaN、""、underfine、null 转换成布尔值为false，其余的都是true

#### 	（二）隐式转换 

​		当运算无法进行下去时，内部就会尝试进行数据类型的转换。

#### 	（三）数字常用的方法

#####         	1、parseInt(a) 将a取整 

​        		parseInt("123.333abc")====>123

#####         	2、parseFloat(a) 取浮点数

​        		parseFloat("123.333abc")====>123.333

#####         	3、Math.round(a) 对a进行四舍五入取整

#####         	4、Math.random() 取[0,1)里面的随机数

​			包含0不包含1。

```
<body>
    <script type="text/javascript">
        // 为抵抗洪水，战士连续作战89小时，编程计算共多少天零多少小时？
        var total = 89;
        var day = parseInt(total/24);
        var hour = 89 % 24;
        console.log("为抵抗洪水，战士连续作战"+day+"天"+hour+"小时");
        // 数字常用的方法：
        // 1.parseInt(a) 将a取整 
        //  * parseInt("123.333abc")====>123
        // 2.parseFloat(a) 取浮点数
        //  * parseFloat("123.333abc")====>123.333
        // 3.Math.round(a) 对a进行四舍五入取整
        // 4.Math.random() 取[0,1)里面的随机数，包含0不包含1。
        console.log(Math.round(123.333));
    </script>
</body>
```

##### 例题：猜数字游戏（法官）

```
<body>
    <h2>猜数字游戏</h2>
    <input type="text" id="num" />
    <input type="button"  value="确定" onclick="compare()"/>
    <script type="text/javascript">
        // 1.法官随机生成1-100整数  
        // Math.random()*100 [0,100)+1===> [1,101)
        // parseInt()
        // 2.获取文本框 document.getElementById("id名")
        // 3.点击确定按钮时
        // * 添加点击事件[onclick="函数名()"]
        // * 定义函数function 函数名(){
        //      3.1 获取到文本框的值
        //      3.2 比较大小，将结果输出
        //  }
        var randomNum = parseInt(Math.random()*100+1);
        // console.log(randomNum);
        var num = document.getElementById("num");
        function compare(){
            var _num = num.value;
            if(_num > randomNum){
                alert("你猜的数字太大了");
            }else if(_num < randomNum){
                alert("你猜的数字太小了");
            }else if(_num == randomNum){
                alert("恭喜你中了500万");
            }else{
                alert("你的智商可能需要充值");
            }
        }
        // 涉及到的知识点
        // 1.生成随机数Math.random()   取整parseInt()
        // 2.获取文本框 document.getElementById("id名")
        // 3.判断语句 
        // if(条件1){
//              满足条件1就执行这里的js代码
//         }else if(条件2){
//              条件2执行
//         }else{所有情况都不满足执行这里的代码}

    </script>
</body>
```

#### （四）逻辑运算

#####         	1、与运算 && 

​      			运算符两侧的值都为true才返回true
      			若与运算左侧的值返回false，直接终止运算

#####         	2、或运算 ||

​       			运算符两侧的值都为false才返回false
        		若或运算左侧的值返回true，直接终止运算

##### 		3、非运算 ！

```
<body>
    <input type="text"  id="year" />
    <input type="button" value="判断闰年还是平年" onclick="panduan()"/>
    <div id="output"></div>
    <script type="text/javascript">
        // 1.获取文本框
        var year = document.getElementById("year");
        var output = document.getElementById("output");
        // 2. 自定义函数{
        //      2.1 获取文本框的值
        //      2.2 进行逻辑运算
        // }
        function panduan(){
            var _year = year.value;
            // 能被4整除而且不能被100整除，或者能被400整除的才叫闰年
            if(_year%4==0 && _year%100!=0 || _year%400==0){
                //3.输出：innerHTML作为元素代码输出
                output.innerHTML = '<span style="color:red;">这是闰年</span>';
            }else{
                output.innerHTML = "这是平年";   
            }
        }
    </script>
</body>
```



#### 	（五）一元运算

​        		++ 自增1
        		前置 ++a,先对a进行自增1，再将a的值返回出去
        		后置 a++,先将a的值返回出去，再对a进行自增1
        		-- 自减1    （使用方法同上）

```
<body>
    <script type="text/javascript">
        var a = 10;
        var b = ++a; 
        console.log(a,b); //11 10
        var i = 1;
        var k = i++ + --i + i-- + ++i;
        //i=1
        //k = 1 + 1 + 1 + 1
        console.log(i,k);
    </script>
</body>
```

#### （六）进制数

```
<body>
    <script type="text/javascript">
        // 五、进制
        // 1.十进制
        // 2.二进制 0b开头，取值为0或1
        var a = 10086; //十进制，取值0-9
        var b = "0b1010";
        // 3.八进制 0o开头，取值0-7
        var c = "0o776";
        // 4.十六进制 0x开头，取值0-9，a-f
        var d = "0xef14";
        // 5.进制转换
        // （1）十进制转多进制 toString(n)
        console.log(a.toString(2));
        // (2) 多进制转十进制 parseInt(num,n);
        console.log(parseInt("1010",2));
        // (3) toFixed(n) 保留n位小数
        console.log(a.toFixed(2));
    </script>
</body>
```

### 六、运算语句

#### （一）程序三大流程

​            		顺序执行：从上到下
            		分支执行：通过条件判断语句，执行相应的代码
            		循环执行：通过循环语句，执行响应的代码

#### 	   （二）分支选择语句if  

​			1.单分支

​				 if(条件){满足条件执行代码}  

​			2.双分支 

​				if(条件){满足条件执行}else{不满足if条件执行这里的代码}   

​			注意：三元运算符(双分支情况可使用)
     	   			条件？满足条件执行这里:不满足条件执行这里

​	 		3.多分支

​				if(条件1){   满足条件1执行 }else if(条件2){满足条件2执行 }else{  不满足以上所有条件执行 }

```
<body>
    <input type="text" id="num" />
    <input type="button" value="判断奇偶数" onclick="jiou()"/>
    <div id="output">
        
    </div>
    <script type="text/javascript">
        // 1.获取到文本框跟#output元素
        // 2.给按钮添加点击事件 [onclick="函数名()"]
        // 3.定义函数 function 函数名(){
        //      获取文本框的值
        //      选择分支语句（奇数、偶数、其他）
        //      将结果输出到output
        // }
        var num = document.getElementById("num");
        var output = document.getElementById("output");
        // var _output = output.innerHTML;
        function jiou(){
            var _num = num.value;
            if(_num % 2 == 0){
                output.innerHTML = '<span style="color:red">这个数是偶数</span>';
            }else if(_num % 2 == 1){
                output.innerHTML = '<span style="color:green">这个数是奇数</span>';
            }else{
                output.innerHTML = '<span>这个数不存在</span>';
            }
            // output.innerHTML = _num%2==0 ? '<span style="color:red">这个数是偶数</span>':'<span style="color:green">这个数是奇数</span>';
        }
        // 常犯错误：
        // 1. = 代表的是赋值号， a = b; a =c;相当于b =c。这种说法是不存在的，从始至终，只改变了a的取值，b没有任何变化。
        

        // 三元运算符(双分支情况使用)
        //  条件？满足条件执行这里:不满足条件执行这里
        var a = 9;
        var b = a>=10? a : a+10;//19
    
    </script>
</body>
```

#### （三）循环语句

​	1、概念

​		当满足一定条件的前提下，反复执行某一段代码（死循环）,直到条件不再满足时退出。

​	2、三大要素

​		变量初始化、条件、变量更新

​	3、while语句

```
			变量初始化
              while(条件){
                  执行的代码;
                  变量更新;
              }		
```

```
案例：打印1-100的奇数
<script type="text/javascript">
        // 1.变量初始化
        var num = 1;
        // 2.条件
        while(num <= 100){
            if(num % 2 == 1){
                console.log(num);
            }
            // 3.变量更新
            num++;
            
        }

```

​	4、do…while语句

```
    <script type="text/javascript">
        // 1.变量初始化
        var num = 16;
        // 2.条件
        do{
            console.log("未成年人请勿观看");
            //3.变量更新
        }while(num>18)
    </script>
```

#### （四）for循环

```
	for(变量初始化;条件;变量更新){执行的代码}
       	for(var i=10;i>0;i--){
             console.log(i);
         }
```

```
案例1：
 <script type="text/javascript">
        // 小王入职薪水10K，每年涨幅5%，10年后工资多少？这10年小王赚了多少钱
        var salary = 10000;
        var total = 120000;
        for(var year=2;year<=10;year++){
            salary = salary + salary * 0.05;
            total = total + salary *12;
        }
        console.log("十年后,隔壁老王的工资是"+salary);
        console.log("这十年，隔壁老王总共赚了"+total);
    </script>
```

```
案例2：
   <script type="text/javascript">
        // 1000-2000年中所有的闰年，并以每行四个数的形式输出
        // 被4整除但不能被100整除，或者被400整除
        var output = document.getElementById("output");
        var n = 1;
        var str = "";
        for(var year=1000;year<=2000;year++){
            if(year%4==0 && year%100!=0 || year%400==0){
                // document.write(year+",");
                str = str + year + ",";
                if(n%4==0){
                    // document.write("<br/>");
                    str = str + "<br>";
                }
                n++;
            }
        }
        output.innerHTML = str;
    </script>
```

#### （五）嵌套循环

​	 执行完里层循环，再执行外层循环。

```
   <script type="text/javascript">
        for(var i=0;i<3;i++){
            for(var j=0;j<3;j++){
                console.log(i,j);//00 01 02  10 11 12 20 21 22
            }
        }
        // 执行完里层循环，再执行外层循环
    </script>
```

#### （六）break与continue

​	break、continue（循环语句使用）
        	 1.break 跳出当前整个循环

​			break一旦运行，当前循环语句里面的代码都不再执行。

​        	 2.continue 仅跳出本次循环，会在此循环中继续下一次循环
        	 3.在多层循环嵌套中，break语句或continue语句只向外跳一层循环。

​			但如果想直接跳出最外层的循环，可以在最外层的的for/while等前面加上标识符（取名），

​        		break和continue后如果带此标识，则可以跳出标识所在的循环。

### 七、函数（一）

#### （一）特点

​	1、函数就是把特定功能的代码抽取出来并进行封装。

​	2、使用函数的好处：

​		（1）可以通过调用使用一段函数；

​		（2）便于维护；

​		（3）程序结构清晰。

#### （二）函数的声明

##### 	1、声明式

​		通过关键字function

​		function  函数名（形参）{js代码}

```
如：function zhengshu(a,b){
        		for(var i=a;i<=b;i++){
        		console.log(i);
        		}
        	}
```

##### 	2、赋值式

​		var 变量(即函数名) = function(){}

```
var zhengshu = function(a,b){
            for(var i=a;i<=b;i++){
                console.log(i);
            }
        }
```

##### 	3、构造函数（不推荐使用）

​		var zhengshu = new Function();

#### （三）函数的执行

##### 	1、直接执行

​		函数名（）；这样为执行函数。

##### 	2、事件驱动

​		ele.事件 = function（）{ }

```
    <input type="text" id="num" />
    <input type="button" id="btn" />
    <script type="text/javascript">
        //2. 获取元素
        var num = document.getElementById("num");
        var btn = document.getElementById("btn");
        btn.onclick = pingfang(4);//！！！错误写法，pingfang(num)代表函数执行，返回了具体值。
        btn.onclick = function(){
            var _num = num.value;
            var result = pingfang(_num);
            console.log(result);
        }       
        // 1.定义平方函数
        function pingfang(n){
            return n*n;
        }      
    </script>
```

#### （四）函数的分类

##### 	1、内置函数

##### 	2、自定义函数

##### 	3、匿名函数

​		function(){   }

​		通常会有驱动事件一起使用，如：ele.onclick = function(){    }

#### （五）声明提前

​	1、执行js代码前，会将所有的声明提前到当前作用域的最前面。

```
	// 这里是细分声明提前的代码
        var newage; //undefined
        var age; //undefined
        newage = age + 1; 
        undefined+1===>NaN
        console.log(newage); //NaN
        age = 17;

    // 这是原代码
        var newage = age +1;
        console.log(newage);
        var age = 17;
```

​        2、当声明提前完成后，才从上往下执行js代码。

​	3、函数声明时，注意避免与变量重名。

```
		var age = 17;   //变量名age
         var age = function(){   //函数名age与变量名重名
             console.log("666");
         }
         age();   //，打印出666
```

​        4、备注：

​		（1）在赋值式中：不能在赋值式声明函数前，先使用函数，这样会报错：zhengshu is not a function。（具体详情请了解声明提前）

```
	zhengshu(); //报错：zhengshu is not a function
     var zhengshu = function(){console.log("666");} 
     
     相当于：
     （1）声明变量
        // var zhengshu;
        // zhengshu(); //报错：zhengshu is not a function
        // var zhengshu = function(){console.log("666");} //分成了两步
        // (2) 对变量赋值
        // zhengshu = function(){console.log("666");}
```

​        	（2）在声明式中： 关键字function声明的函数，可以在函数前后任意调用。

```
（1）声明提前
        // var aaa = new Function();
        aaa();
        // function aaa(){
        //     console.log("8888");
        // } //分成了两步
        //（2）对变量赋值
        function aaa(){
            console.log("8888");
        } 
```

​		（3）当函数执行之后才给变量赋值，则会出现undefined，说明变量声明但未赋值。

```
例题.
     console.log(uname); //undefined,说明变量声明但未赋值
     var uname = "lemon";
     
     相当于：
     	（1）声明变量
        	var uname;
        	console.log(uname); //undefined,说明变量声明但未赋值
        (2) 对变量赋值
       		uname = "lemon";
```

​        备注： 报错后，代码就会终止执行。

​	5、例题：显示和隐藏图片

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <script type="text/javascript">
        window.onload = function(){
            //1.获取元素
            var girlImg = document.getElementById("girlImg");
            var showBtn = document.getElementById("showBtn");
            //3.声明一个变量，告知当前图片是显示还是隐藏
            var show = true;
            //2.点击按钮，隐藏图片
            showBtn.onclick = function(){
                //4.通过show变量，判断一下当前图片的状态
                //=============初级写法=============
                // if(show == true){
                //     girlImg.style.display = "none";
                //     show = false;
                // }else if(show == false){
                //     girlImg.style.display = "inline-block";
                //     show = true;
                // }
                // ==============中级写法=======================
                // if(show){
                //     girlImg.style.display = "none";
                // }else if(!show){
                //     girlImg.style.display = "inline-block";
                // }
                // show = !show;  
                // ===============高级写法================
                // 三元运算符
                girlImg.style.display = show? "none" : "inline-block";
                show = !show;
                
            }
        }
       

    </script>
</head>
<body>
    <img src="../images/32.jpg" id="girlImg" />
    <input type="button" id="showBtn" value="显示隐藏图片" />
</body>
</html>
```

#### （六）作用域

​	1、全局作用域:函数最外层
        2、局部作用域:函数内
        3、全局变量：声明在全局作用域中的变量，在任意位置使用	

```
补充：当函数内没有定义变量，只给变量赋值时，已经默认该变量为全局变量。
如：
 	    var uname = "lemon";
        //var age;一开始外面没有这个定义语句。但函数里的age = 17，相当于已经在函数外定义了age这个变量。
        function aaa(){
            age = 17;
        }
```

​        4、局部变量：声明在局部作用域中的变量，只能在当前函数内使用

​	5、作用域链：当函数访问变量时，根据就近原则从内到外查询变量。

​	6、重复声明的变量无效。

（七）传参

​	1、传参的作用：将值传入函数内；

​	2、形参：函数声明时的参数；

​	3、实参：实际参数，函数执行时的参数；

​		在js中，实参与形参的个数可以不一样。

​	4、数组Array[  ]

​		一个变量存储多个值。

​		（1）获取数组的某个信息，通过索引（从0开始）获取：数组名[索引名]；

​		（2）属性length：数组的长度。用.length获取。如：arr = arr.length;获取数组arr的长度。length-1获取到数组中最后一个值。

​		（3）arguments   类数组，数组的一个类型。

​	5、函数的传参（基本数组类型与应用数据类型的区别）

​		（1）基本数据类型传参		

```
		var a = "laoxie";
        function show(b){
            b = "lemon"; //b赋值相当于已经被定义为全局变量。此时b的值与a的值是不相关的。
            console.log(b);//lemon
         }
         show(a);
         console.log(a);//laoxie
```

​		（2）引用数据类型传参（参数为数组，则传递的是地址，若此时赋给形参的值发生改变，则原来的数组的值也发生改变）

```
var arr = ["laotian","laoxie","xiaoxie"];
function show(brr){
    brr[2] = "lemon";
    console.log("brr:"+brr);//输出“lemon”
}
show(arr);
console.log("arr:"+arr); //lemon
```

（八）返回值 return

​	1、作用：将函数内部的值返回出去，注意！外部需要用一个变量来接收；

​	2、如果函数没有return，执行完后返回值为undefined；

​	3、可用return退出当前函数，因为执行完return后，函数内的代码不会继续执行；

​	4、一般不会在函数声明的时候直接打印成绩，而是将值返回出去。

### 八、函数（二）

#### 	（一）this

​		当前对象，取决于谁调用了这个函数

​		1、执行函数的对象（普通函数）一般都是window；

​		2、事件驱动执行函数（事件触发的函数），那么此时的this指向执行函数的对象（事件源对象）。

```
<input type="button" id="btn" />
    <script type="text/javascript">
        var btn = document.getElementById("btn");
        // (一)this 当前对象，取决于谁调用了这个函数
        // 1.执行函数的对象一般都是window
        // 2.事件驱动执行函数，那么此时的this指向执行函数的对象。
        function add(){
            console.log(this);
        }
        btn.onclick = add;
    </script>
```

#### 	（二）递归

​			1、函数自己执行自己（在自己的函数里面执行，即函数名()；）。需要一个退出函数return的条件，若不存在退出条件会死循环。

​			2、若进行死循环则会报错：Maximum call stack size exceeded 超出最大的内存

```
1、递归前输出，正向输出
		var num = 10;
        function zijian(){
             num--;
             if(num <= 0){
             	return;
             }
             console.log(num);//递归前输出，正向输出 ，此时num-- == 9，输出9
             zijian(); //递归
         }
         	zijian()；
```

```
2、递归后输出，按最后一次递归的值输出
	var num = 10;
	function zijian(){
            num--;
            if(num <= 7){
            	return;
            }
            zijian();
            console.log(num);//递归后输出，按最后一次递归的值输出，此时 num--得到9，递归再一次num--得到8，再一次递归num-- 得到7，满足条件，return；输出7. 
        }
       	 zijian();
```

​			注意：把判断放在自减的后面，否则会进入无限的自减循环，不能进行下面的步骤。		

​	3、例题：阶乘的计算

```
    <script type="text/javascript">
        function factorial(num){
            if(num == 1 || num==0){return 1;}
            return num*factorial(--num);
             // !!!注意区分 --num（先对num进行自减再返回值） 
            // 与num--（先返回值再对num进行自减，若先返回值，则相当于num得到参数后就直接返回，再接收再返回进入死循环，不会执行后面 -- 的操作。）
        }

        console.log(factorial(4));
        //num=4;
        // factorial(--num)  // num=3 factorial(3)  
        // factorial(num--)  //factorial(4) num=3;
    </script>
```

​		4、例题：斐波那契数列	

```
    <script type="text/javascript">
        // 1,1,2,3,5,8,13,21  斐波那契数列为 前两个的数之和等于第三个数
        // fib(n) = fib(n-1) +fib(n-2)
        function fib(n){
            if(n==1 || n == 2){
                return 1;
            }
            return fib(n-1) +fib(n-2);
        }
        console.log(fib(5));
    </script>
```

#### 	（三）数据类型

​		1、基本数据类型 number

​			包括数字、NaN  、string:"";  、Boolean：true 、false

​		2、特殊数字类型：null、undefined

​			console.log(null+2);       //2
        		console.log(null == undefined);         //true

​		3、引用数据类型：Object、Array、Function...

​		4、数据类型的判断： typeof

​			typeof(null);          //object ====>!!!!
        		console.log(typeof typeof 10);          //string

​		5、数据类型转换

​			Boolean(0、NaN、""、null、undefined) =>false 

#### 	（四）回调函数

​		1、百度定义（通过[函数指针](https://baike.sogou.com/lemma/ShowInnerLink.htm?lemmaId=7627909&ss_c=ssc.citiao.link)调用的函数。如果你把函数的指针(地址)作为参数传递给另一个函数，当这个指针被用为调用它所指向的函数时，我们就说这是回调函数。 ）

​		2、理解：若现在有两个函数，函数1需要调用函数2中的值，则将函数2作为函数1的参数传入函数1中，这样函数1就可以通过参数来调用函数2中的操作。

```
   // (三)回调函数
        function uname(fn){
            // var fn = show；
            fn("laoxie");
        }//甲
        function show(uname){
            // var uname = "laoxie";
            console.log(uname);
        }//乙       
        //若想执行乙，但是我需要甲的一个变量。选择在甲函数里面执行乙函数
        uname(show);

```

### 九、数组

#### 	（一）数组的定义

​		1、字面量 var arr = [ ];

​		2、通过构造函数法   var  arr = newArray（）；

​		（1）var arr = new Array();只声明（创建一个空数组）

​		（2）var arr = new Array(n);创建一个长度为7的数组

​		（3）var arr = new Array("laoxie");声明的同时赋值

​		3、每一项数组都可以保存任何类型的数据，成为数组的元素。

#### （二）数组的操作（增删查改）

​	1、数组的读取与写入

​	（1）数组的索引 arr[idx] idx取值从0开始

​	（2）数组元素的读取(查)与写入(改、增,其实就是赋值)

​	（3）数组元素的删除（修改数组的长度 arr.length）

​	（4）遍历数组（数组的长度arr.length，索引的取值为0到arr.length-1）

```
 <script type="text/javascript">
        // 创建一个数组，存放50个三位数的随机数
        // 1.创建数组
        var arr = [];
        // 3. for循环50次
        for(var i=0;i<50;i++){
            // 2. 生成3位数的随机数
            var randomNum = getRandomNum(100,999);
            // arr[i] = randomNum;//（1）
            // arr[arr.length] = randomNum; //(2)
            // (3)数组的方法
            arr.push(randomNum);
        }
        console.log(arr);
        // 练习:函数实现：创建一个数组，存放n个三位数的随机数！！
    </script>
```

#### （三）数组的方法

##### 	1、增删改（原数组被改变）

​		（1）push（item，item）往数组尾部添加一个或多个元素；

​		（2）unshift（item，item）往数组头部添加一个或多个元素；

​		（3）pop（）删除数组的最后一个元素；

​		（4）shift（）删除数组的第一个元素；

​		（5）splice（idex，delNum,item）

​			①idex代表索引

​			②delNum代表要删除的元素的数量

​			③item表示要添加的元素

```
		// var res = arr.shift();
        // arr.splice(2,2);//删除功能
        // arr.splice(3,0,"lemon");//添加功能
        // arr.splice(2,1,"lemon");//修改功能
```

​		（6）slice（start，end）切割

​			将原数组从start开始切割刀end（不包括end所对应的元素），通常用来赋值数组。返回一个被裁减后的新数组。	

​			①如果省略end参数，则截取到数组的最后一项；

​			②支持负数，若为负数，则-1表示最后一个索引，以此类推；

​			③原数组不会被改变。

​		（7）join（分隔符）拼接字符串

​			将数组通过分隔符拼接成字符串。

​			①若分隔符的参数省略，默认会将数组的每一项用逗号隔开，返回字符串；

​			②若分隔符的参数存在，则会将数组每一项用分隔符隔开‘

​			③arr接收完所有内容后，再用join转成字符串，若中间不用分隔符，则join（" "），在join的参数里加一个空字符。

​		（8）concat（） 数组合并，返回一个新数组，这个数组是由调用这个方法的数组和参数组成的。原数组不变。

```
	console.log(arr.concat(arr2,arr3));
```

| 方法名    | 作用                         | 返回值                         |
| --------- | ---------------------------- | ------------------------------ |
| push()    | 增（尾部）                   | 新数组的长度                   |
| unshift() | 增（头部）                   | 新数组的长度                   |
| pop()     | 删（最后一个）               | 被删除的数组                   |
| shift()   | 删（第一个）                 | 被删除的数组                   |
| splice()  | 增+删                        |                                |
| slice()   | 切割（复制数组）             | 被切割后的字符（原数组不改变） |
| join()    | 将数组通过分隔符拼接成字符串 | 数组通过分隔符拼接成的字符串   |
| concat()  | 数组合并                     | 返回一个新数组                 |

##### 	2、遍历（es5新增数组方法）

​		（1）遍历方法

​			①forEach(fn)   遍历方法，for循环没有太大差别，比for循环方便；	

```
 var arr = [1,2,3,666];
     arr.forEach(function(item){
          console.log(item);
     })
```

​			②map（fn）返回一个数量相等的数组，内容是什么取决于在fn中返回的值。

```
var arr = [1,2,3,666];
        var res = arr.map(function(item,idx){
            return item*1.2;
        })
        console.log(res);
```

​			③filter（fn）利用这个方法可以对数组元素进行过滤筛选。存放执行fn后返回true的数组元素。

```
// 取出小于10的数组元素，并组成新数组
        var arr = [15, 16, 10, 15, 9, 0, 2, 17, 8, 18];
        var res = arr.filter(function(item){
            return item<10;
        });
        console.log(res);
```

​			④some(fn) 返回布尔值，如果该函数对任何一项返回 true，则返回true；

​			⑤every(fn)  返回布尔值，如果该函数每一项都返回 true，才返回true。	

​		（2）fn的三个参数：

​			①第一个参数，代表数组的每一项元素item；

​			②第二个参数，代表数组的每一项的索引idx(i)；

​			③第三个参数，代表当前的数组 arr。

##### 	3、归并方法

​		（1）reduce(fn[,原始值])

​		（2）fn的参数
        		①-prev：上一次的返回值。
       			②第一次执行函数时，会将原始值作为prev的值；若原始值缺省，则拿当前数组的第一个元素作为prev的值。
        		③- cur：当前值，
        		④- index：索引值，
        		⑤- array：当前数组，
       			⑥*原始值可以缺省。

##### 	4、静态方法Array.isArray()（判断是否为数组）

##### 	5、索引方法

​		（1）indexOf(keyword [,startIndex]):返回keyword所在数组中的索引值。

​			①- keyword: 要查找的项，

​			②- startIndex：开始查找位置的索引，该参数可选，默认0

​			③如果数组不存在keyword，则返回-1	

```
应用：（1）
        // if(arr.indexOf(keyword) != -1){
        //      //说明数组中存在这个值
        // }
        // （2）
        //  if(arr.indexOf(keyword) >= 0){
        //      //说明数组中存在这个值
        // }
```

​		（2）lastIndexOf(keyword,[startIndex]):返回keyword所在数组中的索引值。

#### （四）数组排序

​	1、冒泡排序法

​		（1）遍历元素，跟其下一个元素对比（每一论的操作）；

​		（2）把最大的逐个往后排列；

​		（3）外层循环，代表的是遍历的次数。

```
 			var arr = [10,2,444,245,1];
        // （1）遍历数组
        // for(var i=0;i<arr.length-1;i++){
        //     for(var j=0;j<arr.length-1;j++){
        //         // （2）判断arr[j]>arr[j+1],互换位置,通过一个过渡变量
        //         if(arr[j] > arr[j+1]){
        //             var current = arr[j];
        //             arr[j] = arr[j+1];
        //             arr[j+1] = current;
        //         }
        //         console.log(666);
        //     }
        // }
```

```
完善算法：外层i为遍历次数，i从0开始计算，到i=1的时候，前面一次遍历可以不用再进行一次，因此可以少比较一次。所以得出结论。每i轮少比较i次。因此j<arr.length-1-i。
        for(var i=0;i<arr.length-1;i++){
            for(var j=0;j<arr.length-1-i;j++){
                // （2）判断arr[j]>arr[j+1],互换位置,通过一个过渡变量
                if(arr[j] > arr[j+1]){
                    var current = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = current;
                }
                console.log(666);
            }
        }
        console.log(arr);
```

​	2、选择排序

​		（1）把当前索引的值，分别跟后面所有的元素对比；

​		（2）把最小的逐个往前排列。

```
var arr = [10,2,444,245,1];
        for(var i=0;i<arr.length-1;i++){
            for(var j=i+1;j<arr.length;j++){
                if(arr[i]>arr[j]){
                    var current = arr[i];
                    arr[i] = arr[j];
                    arr[j] = current;
                }
                console.log(666);
            }
        }
        console.log(arr);
```

​	3、快速排序法（递归）

​		（1）利用递归函数实现排序

​		（2）每次获取数组的中间元素cItem

​		（3）把大于和小于cItem的元素分别放在arrGt 和arrLt两个数组中；

​		（4）函数自己执行自己进行递归，将arrLt[]以及arrGt[]两个数组中的数重新进行排序，最后同时用concat进行组合。

```
 function fastSort(arr){
            //5.避免死循环，满足数组长度小于1时，直接返回数组
            if(arr.length <= 1){
                return arr;
            }
            //1. 找出数组中间位置元素
            var cIdx = parseInt(arr.length/2);
            // 2. 通过splice(),改变原数组(去掉了中间那个数)。返回值为被删除的元素
            var cItem = arr.splice(cIdx,1);
            // 3.声明两个数组
            var arrGt = [];
            var arrLt = [];
            // 4.遍历arr,大于cItem的值，放在arrGt。小于的话放在arrLt
            for(var i=0;i<arr.length;i++){
                if(arr[i]>cItem[0]){
                    arrGt.push(arr[i]);
                }else if(arr[i] < cItem[0]){
                    arrLt.push(arr[i]);
                }
                console.log(666);
            }
            return fastSort(arrLt).concat(cItem,fastSort(arrGt));//fastSort();执行======>函数自己执行自己进行了递归，将arrLt[]以及arrGt[]两个数组中的数重新进行排序，最后同时用concat进行了组合。
        }
        console.log(fastSort(arr));
```

​	4、sort排序法

​		将数组中的元素排序，返回排序后的数组。

​		（1）默认以字符串的排列方式（转换成ASCII码进行对比）；

​		（2）sort(function(){return a-b;})  数字从小到大排序；

​		（3）sort(function(){return b-a;})  数字从大到小排序。

#### （五）数组的复制

​	1、基本数据类型的传递

​		var a = 10; var b = a; var b = "哈哈";console.log(a,b);

​		输出：a  10  ；b  哈哈

​	2、引用数据类型

​		传递的是地址，原数组的值会跟着被改变。

```
		var arr1 = [10,20,30];
        var brr = arr1;
        brr[0] = "lemon";
        console.log("arr1",arr1);===========》lemon，20，30
        console.log("brr",brr);=============》lemon，20，30
```

​	3、如何复制数组，且不影响到原数组？

​		（1）遍历，通过push()把原数组的元素推入到新数组中；

​		（2）通过slice（0）将原数组的元素切割后再铺上到新数组中，使用slice原数组不受影响。

​	4、注意事项：

​		错误写法：res = res.push(arr[i]); 原因如下：
                （1）先执行push() ====>  res = [9];（push返回的是新数组的长度）
                （2）执行完毕后将返回值（新数组的长度）赋给res。===>res = 1;
                （3）会报错： res.push is not a function

​			报错原因：

​              			① 方法名字写错
                		②该变量没有这个方法



### 十、对象

#### 	（一）对象的定义

​		1、字面量  var 变量名 = {键：值，键：值}；

​		2、构造函数  var  变量名 = new Object()；

#### 	（二）对象的操作

​		1、通过键值对，操作对象的两种写法

​			（1）对象.具体的键；

​			（2）对象[“具体的键”]

​		2、添加、修改键（对对象的键进行赋值）

​		3、删除键      delete

​		4、读取键对应的值

​			data[i]    获取data数组中i索引所在的位置

​			data[1].键      获取该对象键所对应的值

​		5、数组和对象的组合		

```
<script type="text/javascript">
        var arr = [{
                    name:"老谢",
                    age:48,
                    hobby:"嘤嘤嘤"
                },
                {
                    name:"老田",
                    age:18,
                    hobby:"对lemon好"
                },
                {
                    name:"老梦",
                    age:17,
                    hobby:"对老谢好"
                }];
        console.log(arr[0].age);


    </script>
    
    例题：根据数据生成一个商品列表。
```

#### 	（三）对象的遍历

​		 1、for(var 键 in 对象){操作每个键值对}

​		 2、若变量为被遍历的键，则只能用中括号来获取。

### 十一、字符串String

#### 	（一）创建字符串

​		1、字面量 var str = "";

​		2、构造函数 var str = new String();

#### 	（二）字符串的操作

​		1、属性：length 获取字符串的长度；

​		2、获取索引对应的值：

​			（1）str[idx] ===>es5才出现；

​			（2）charAt(idx)。

​		3、查找索引方法：

​			indexOf(keyword[,startidx]);

​			返回一个数字，从开头/尾部向后查找字符串keyword第一次出现的位置,如果没找到返回-1。

​		4、 字符串拆分成数组split

​			split(分割符)根据分割符，把字符串拆分成数组；

​		5、字符串的替换

​			（1）原字符串.replace(str||regExp,替换的值) 返回被替换后的字符串，原字符串的值不受影响！

​			（2）字符串的替换只能执行一次，不能够进行全局匹配，如果需要全局匹配，则应使用正则表达式。

​		6、截取方法 

​			(1) slice(start[,end]) 截取start到end(不包括end)的字符串，支持负数；

​			(2) substring(start[,end]) 截取start到end(不包括end)的字符串；

​			(3) substr(start,length) 索引支持负数，len为截取的数量。

​		7、其他方法

​			（1）- toLowerCase()：转换成小写；

​			（2）- toUpperCase()：转换成大写；

​			（3）trim()：删除前后所有空格，返回新的字符串。

#### 	（三）正则表达式

​		1、正则表达式()

​			（1）var reg = /值/gi;

​			（2）var reg = new RegExp("值","gi");

​				* var reg = new RegExp(变量,"gi");

​		2、正则表达式的参数

​			（1） g 全局匹配

​			（2） i 不区分大小写

#### 	（四）字符编码（了解）

​		1、"字符串".charCodeAt(索引) ： 得到字符串中索引对应的值，对应的字符编码；

​		2、String.fromCharCode(字符编码的值) 通过字符编码，得到对应的字符。

#### 	（五）获取ul参数

```
 <script type="text/javascript">
        // 参数转成对象输出 {name:'laoxie',age:18,sex:male}
        var url = 'https://www.qq.com/s?name=laoxie&age=18&sex=male&';
        // 1.获取到？所在的索引值
        var idx = url.indexOf("?");
        // 2.截取参数
        var params = url.slice(idx+1,-1);
        // 3.参数数组
        var paramsArr = params.split("&");
        var obj = {};
        // 4.对参数数组进行遍历
        paramsArr.forEach(function(item){
            var arr = item.split("=");
            obj[arr[0]] = arr[1];
        })
        console.log(obj);

        //item:   "name=laoxie".split("=")   ===>["name","laoxie"]  ===>arr[0]: arr[1];


        // obj[age]
        // age
    </script>
```

### 十二、Math&Date

#### （一）Math

​		1、属性 PI

​		2、 2.方法
        		（1）四舍五入取整Math.round()
        		（2）向上取整Math.ceil()
        		（3）  向下取整floor(11.8) //11 
       				* Math.ceil(-11.3) //-11 向上取整

#### （二）Date

##### 	1、创建时间和日期

```
//1）创建当前时间的日期和时间
var d = new Date();//得到的是代码执行时的时间（本地时间）

//2）创建指定日期的时间和日期
var d = new Date("2015/08/22");
var d = new Date(56521211021);//参数为距1970-1-1零时的毫秒数
```

##### 	2、获取/设置时间

​	（1）获取年月日

- ​	getFullYear()/setFullYear(2014)

	 ​	getMonth()/setMonth(8)注意：获取月份是从0开始的

	 ​	getDate()/setDate(25)

  （2）获取星期

- ​	getDay() 0-6:星期天-星期六

  （3）获取时分秒

	 ​	getHours()/setHours()

	 ​	getMinutes()/setMinutes()

	 ​	getSeconds()/setSeconds()

	#### 	3、日期处理

- getTime()/setTime()：获取/修改某个日期自1970年1月1日0时以来的毫秒数
- toLocaleDateString(); 以特定地区格式显示年、月、日
- toUTCString(); 转换成UTC时间

##### 4、ES5方法

- Date.parse(“2015-08-24”)//返回指定日期距1970-1-1零时的毫秒数
	 ​	PS：转换格式默认支持2015-08-24或2015/08/24
- Date.now();//返回执行这行代码时距1970-1-1零时的毫秒数

##### 5、延迟与定时器

- setTimeout(fn,200)：两百毫秒后执行fn这个函数（只执行一次）,返回一个id标识
- clearTimeout(timeoutID)：清除指定id标识的延迟操作
- setInterval(fn,30)：每隔30毫秒执行一次fn这个函数,返回一个id标识
- clearInterval(intervalID)：清除指定id标识的定时器操作

```
 var timer = setTimeout(function(){
        //2s后执行这里的代码
    },2000);

    //清除
    clearTimeout(timer);
```

### 十三、BOM

#### （一）window

​	window对象是BOM的核心, 是最顶层的对象，所有对象都是通过它延伸出来的

1、常用属性：

​	浏览器窗口尺寸
		innerWidth/innerHeight, //表示浏览器窗口”可视区域”尺寸
		outerWidth/outerHeight //表示整个浏览器窗口的尺寸
	滚动相关
		scrollX/scrollY //获取浏览器窗口滚动条滚动过的距离
		scrollTo(x,y) //设置浏览器滚动距离
		scrollBy(xnum,ynum) //设置基于当前位置滚动的距离，可以为负数

2、方法：

- alert（）弹窗
- prompt（question，default），返回值为输入框的值或null
- confirm（）确认框，返回布尔值（确定为true/取消为false）
- open（"域名"，"名字"，"属性"）
- close（）关闭窗口
- print（）调出打印对话框

3、window对象常用事件

- onload //页面资源全部加载完成后触发这个事件
- onscroll//窗口滚动条滚动时触发
- onresize //窗口大小改变时触发

#### （二）location（重要）

属性：

- hash 设置或返回从井号 (#) 开始的 URL（锚）==>哈希值。
- href 设置或返回完整的 URL。
  - 修改href值 ：location.href = "html2/aa.html?id=1&name=iphone7&price=4000"
- search 设置或返回从问号 (?) 开始的 URL（查询部分）。
  - 参数的作用：传递到另一个页面告知具体的显示信息
- encodeURI();//转码,将中文、特殊字符转成一定码
- decodeURI();//解码,将码转回中文、特殊字符

#### （三）history（重要）

​	历史对象,包含窗口的浏览历史，可以实现后退 。

​	1、属性：
		length 返回浏览器历史列表中的 URL 数量。
	2、方法：
		back() 加载 history 列表中的前一个 URL。
		forward() 加载 history 列表中的下一个 URL。
		go() 加载 history 列表中的某个具体页面，支持负数。

```
history.go(2);//向前两个页面
history.go(-2);//后退两个页面
```

（四）navigator（了解）