

# HTML 5 学习笔记

## 一、HTML相关知识+标签

### 一、基础概念

##### （一）建站流程

​	1.注册域名--网址-如：http//www.baidu.com
	2.租用空间（用于存放css文件或图片）
	3.网站建设：制作页面（将psd图还原成一个网页，数据是动态的（不是固定的））
		psd图：图层分离的图片，一般都是留作存档
	4.网络推广
	5.网络维护

##### （二）HTML

​	指的是超文本标记语言（Hyper Text Markup Language）---可以实现点击跳转
标记

​	一套标签组成的语言

##### （三）XHTML 

​	Extensible HTML可扩超文本标记语言（标识语言）

​	HTML 5指第五次重大修改*

##### （四）发展历程

（待补充）

##### （五）W3C

 	 万维网联盟  world wild web consortium    ---制定结构html和表现css
ECMA 欧洲电脑场商联合会   ---制定js

##### （六）web标准

​	1.结构---人的身体---Xhtml     Xml
	2.表现---人的衣服---css
	3.行为---人的动作---js       ECMAScript

### 二、sublime的使用

##### （一）快捷方式

    <!--sublime的使用：
    1.菜单-打开文件夹-site文件夹
    2.鼠标移动到指定文件夹-右键新建文件（后缀名  .html）
    3.快捷方式：
        ！+tab  快速生成结构
        ctrl+s  保存
        ctrl+c  复制
        ctrl+x  剪切
        ctrl+v  粘贴
        ctrl+z  返回上一步
        ctrl+y  返回下一步
        ctrl+？ 快速生成注释
        ctrl+h  将所有相同的标签名置换为另一个标签名
        f1、f2打开谷歌浏览器
        f3  打开IE浏览器
        标签名+tab
        tab  缩进
        shift+tab   往前缩进
    
    4.右键-在浏览器打开
    控制台的使用：
        找到制定元素-右键检查
        f12-通过左上角的鼠标图标，找到指定元素所在的代码行
    5.table>tr*10>td*10-按table键，出现十行十列

##### （二）标签

###### 	1、标题标签  h1-h6.

​	在直观上字体越来越小，在语义上越来越轻，一级标题最好一个页面只用一次；

###### 	2、段落标签 p

​       	      备注：浏览器解析时，会将多个空格及换行解析成一个空格

######         3、换行标签br

​	单标签<br/>

######         4、标识符

​		 &nbsp；空格  &lt；小于号   &gt；大于号
         	备注：空格的大小不等于文字大小，但是空格大小受文字大小影响。

######         5、加粗标签

<b></b>和<strong></strong>
                备注：视觉标签<b></b>  语义标签<strong></strong>

######    	6、倾斜标签 i 、em

​		<i></i>、<em></em>

​                备注：视觉标签<i></i> 语义标签<em></em>

######          7、分割线标签 hr

​		单标签<hr />

######          8、删除线标签

​		 <s></s> <del></del>

######          9、列表标签

​        （1）无序列表  ul（unordered list）包括li（list item列表项）ul只能嵌套li

​	（2）有序列表 ol(ordered list)包括<li></li>   

​	 ( 3 )自定义列表dl（definition list）

​		dt（definition term 自定义列表项）

​		++dd（definition description对自定义列表项的描述）

###### 10、图片标签

​	 <img src="" alt="" />
        [src]-引入图片的路径  ../返回上一层目录
        [alt]图片无法加载出来时呈现的文字 
        [title]鼠标悬停时出现的文字

###### 11、锚链接、超链接

​	 <a href=""></a>
        [href]跳转的路径，要完整的域名、#表示不跳转或者跳到当前页面的最顶端
        a[href][target="_self"][target="_blank"] 
        [target]跳转的窗口  属性值：_self 默认在当前窗口跳转  _blank在新窗口打开

######     12、表格 标签

​	   table>tr行>td单元格 
        	table
                [border]给单元格加上边框，一般设成border=“1”；
                [cellspacing]单元格与单元格之间的距离
                [cellpadding]单元格的内填充-单元格的内容与边框之间的距离
                [width]宽度
                [height]高度

​	td[colspan]合并列       rowspan[合并行]

######    13、form>input表单控件

​            form：
            [action 提交到的input表单控件后台地址]
            [method 提交方式]
            [name 表单名字]文本框
            input：
                    [type]类型：
                    [text  文本框]
                    [password 密码框]
                    [radio 单选框]
                    [checkbox  多选框]
                    [checked 默认选中]
                    [submit  提交按钮]
                    [reset   重置按钮]
                    [button  普通按钮]
                    [name]同一组单选框或多选框要起一样的名字
                    [value]给表单加内容

######       14、form>select下拉框>option选项[value][selected 默认选中]

######       15、form>textarea文本域[cols列][rows行]



### 三、css基础

##### （一）css简介

​	css cascading style sheets 层叠样式表

​	层叠性：给同一个元素添加相同的css属性，属性值会覆盖问题。

##### （二）css语法

​	css语法由两部分组成：选择符、声明  即  选择符{属性：属性值}；

##### （三）样式的建立

​	内部样式   外部样式   内联样式

###### 1、内部样式

​	表语法：<style type="text/css">/*css语句*/</style>

​	注：使用style标记创建样式时，最好将该标记写在<head></head>;

​	【个人说明：内部样式写在style标签里面，如果要给bady里的div加样式则写---div{样式}  ，若是给h1添加内部样式，则写h1{样式} 】

###### 2、外部样式

​	外部样式的建立及调用a:外部样式表的创建b:外部样式表的导入

*方法 一<link rel="stylesheet" type="text/css" href="目标文件的路径及文件名全称" />

​	【个人说明：链接到css文件里获取样式，即把样式写在css文件中，写法与内部样式相同】

​	*方法二<style type="text/css">@import url(目标文件的路径及文件名全称);</style>注：@和import之间没有空格 url和小括号之间也没有空格；必须结尾以分号结束；行间样式，行内样式，嵌入式样式语法：<标签 style=“属性：属性值;属性:属性值;”></标签>

###### 3、内联样式

直接在选择符里添加属性和属性值，如

​		`<div style="width:300px;height:300px;background-color:red;">`直接在div里添加style。

##### （四）样式表的作用域

​	 行内样式的作用域是当前标签，内部样式的作用域 是当前文件，外部样式表的作用域是有关联的所有文件。

三种样式表的优先级：
                    内联样式>内部样式 ,内联样式>外部样式
                    内部样式与外部样式谁写在后面，就覆盖前面样式表的相同元素的相同属性

##### （五）选择器

######            1、标签选择器，元素选择器

​		通过标签获取到元素

######            2、类选择器

​		通过类名（class名）获取到元素
                    对应的html属性为class[class=""]-给元素添加类名（相当于绰号）
                    命名规则：英文开头，包含数字、下划线、-（中杠）

######            3、id选择器

​		通过#id名获取到元素
                [id=""]给元素添加id名（身份证号码），不可以重复

######            4、通配符选择器

​		 *{} 获取到页面上的所有元素

######            5、群组选择器（并集选择器）

​		将多个基本选择器用逗号隔开，表示都获取到

###### 	   6、伪类选择器  

​		用冒号开头

            /*（1）a:link 锚链接被访问前出现的样式*/
            a:link{background-color: yellow;}
            /*（2）a：visited 锚链接被访问后出现的样式*/
            a:visited{background-color: red;}
            /*（3）a：hover  鼠标悬停在E元素上出现样式*/
            a:hover{background-color:green;}
            /*(4)a:active 鼠标点击E元素时出现样式*/
            a:active{background-color:pink;}
            /*以上四个顺序不能调，否则会乱，记成lv-ha*/
###### 		7、选择器的优秀级

​            ！important>内联样式>id选择器>类选择器（伪类选择器）>标签选择器>通配符选择器
          *{color:green;}  通配符选择器(前面为星号)
            div{color:red;}   标签选择器（前面为标签）
            **.**fenshua{color:orange;} 类选择器（前面为一点）
            #jiang{color:yellow;}  id选择器（前面为井号）

##### （六）权重0000

只有作用到同一个元素上才能比较权重
                第一各数字代表important或者行内样式有多少个
                第二个数字代表id选择器有多少个
                第三个数字代表类选择器有多少个
                第四个数字代表标签选择器有多少个
                以上四个没有则写0，最后比较大小
                继承的权重最低为0000

                id选择器井号 #
                类选择器点 .
                标签选择器标签 如div
    		/*.baba div{color:yellow;}
              对于儿子来说，权重是0011*/
            /*.baba .erzi{color:green;} 
            对于儿子来说，权重是0020*/
            /*#father .erzi{color:red;} 
            对于儿子来说，权重是0110*/
            /*0110>0020>0011,权重也越来越小*/
            
            #grandpa #father{color:pink;}
            /*#grandpa #father{color:pink;}
                对于儿子来说，继承爸爸的权重，因此权重是0000
                对于爸爸来说，权重是0200
            */
           /*#father #son{color:black;}
                如果要把儿子的权重增加，则在加一个#son
            */
### 四、文本、边框、列表、背景、浮动

##### （一）字体属性  font

######             1、字体大小 font-size 

​                * 默认字体大小为16px
                * 最小的字体大小为12px
                * 9pt=12px 12pt=16px

######             2、字体加粗 font-weight

​                * 属性值： normal(100-500)默认正常 				bold(600-900)加粗  	bolder更加粗

######             3、字体倾斜 font-style

​                * 属性值： normal默认正常  italic倾斜 

######             4、字体家族 font-family

​                * 中文字体或者多个单词组成的字体要加双引号
                * 多个字体家族用逗号隔开

######             5、字体颜色 color

​                * 属性值： 英文单词    十六进制
                * 十六进制表示：#000000 前两个0红色，中间两个0绿色，后2个是蓝色

​		每一位的取值为0-9 a b c d e f 

    	    font-size:20px;
            font-weight: bold;
            font-style:italic;
            font-family: "Times New Roman","楷体";
            color:#000000;
##### （二）文本属性 text

​            1.设置文本大小写 text-transform
                属性值： none默认不转换   lowercase全部小写 uppercase全部大写 capitalize首字母大写

##### （三）文本修饰text-decoration

​            属性值： none默认不修饰   

​			    underline下划线  

​			    overline上划线  
          		    line-through删除线   

##### （四）首行缩进 text-indent

​                单位: em以当前字体大小为基准
                可以取负值

```
div{
            width: 300px;height: 300px;background-color:red;
            font-size:20px;
            text-indent:-11em;
        }
```



##### （五）字间距letter-spacing

##### （六）词间距 word-spacing

​		(以空格作为分隔符)

##### （七）行高line-height

​	文字在行高的中间。以下代码实现文本居中

```
div{
            width: 400px;
            height: 400px;
            background: red;
            line-height:400px;
            text-align: center;
        }
```



##### （八）文本在容器中的水平对齐方式 text-align

​           属性值：left默认左边  center中间   right右边 justify自动调整（英文两端对齐）

##### （九）行内元素在垂直方向的对齐方式 vertical-align

​           属性值：baseline默认基线对齐    middle中线对齐    top顶线    bottom底线 
            一般用在图片与文字垂直居中对齐

##### （十）列表属性 list-style

######             1、列表样式类型 list-style-type

​               属性值：disc实心圆  circle空心圆  square方块 			none去掉

######             2、列表样式图片 list-style-image:url("")；

######             3、列表样式位置 list-style-position

​               属性值：outside默认列表样式在li内容外边   inside在li内容里面。
            *总属性:list-style:1||2 3;可以缺省值
           	 用得最多 list-style:none。

##### （十一）边框属性border

######                 1、边框宽度 border-width

######                 2、边框样式 border-style

​                    *属性值： solid实线    dashed虚线  dotted点线  double双线
                3.边框颜色 border-color
                总属性：border: 1 2 3;
                border-方位（top上、bottom下、left左、right右）:1 2 3
                border-方位-分属性

​	    `border:3px dotted red;`
            `border-left:5px solid yellow;`
            `border-right-color:blue;`

##### （十二）背景属性background

​        1.背景颜色 background-color
        2.背景图片 background-image:url("")
           * 当容器尺寸大于背景图片尺寸时，背景图片会重复平铺满整个容器
           * 当容器尺寸小于背景图片尺寸时，背景图片会丢失一部分
           * 当容器尺寸等于背景图片尺寸时，刚好放下
        3.背景平铺 background-repeat
            * 属性值：repeat默认平铺  no-repeat不平铺  repeat-x水平方向平铺 repeat-y垂直方向平铺
        4. 背景图片在容器中的定位 background-position:水平方向 垂直方向;
      *属性值： 数值(往右为正、往下为正)、方位（left\center\right top\center\bottom）
	5.背景图片的固定background-attachment
           属性值： scroll默认滚动  fixed固定

#####  （十三） 浮动 float

/*如果块级元素设置了宽度，右边多的位置会默认由margin填充*/所以需要用浮动。

​        1.属性值： left左浮动   right右浮动  none默认不浮动
        2.特点：
            （1）浮动的元素会脱离标准流
            （2）浮动的元素相当于行内块级元素（一行显示多个、可以设置宽高）
            （3）当浮动的元素换行摆放时，它垂直方向的位置会参考上一个元素的最低点。

       3. 浮动的起源：文字环绕图片   img{float: left;}
    
          ```
          .box{width: 400px;height：400px;border:1px solid #ccc;}
           .box img{opacity:0.2;float: left;}
           .box p{background-color: red;}
          ```

### 五、盒模型

##### （一）概念

​       1.盒模型=内容content+内填充padding+边框border+外间距margin
        2.width、height不是指盒子的大小，而是内容content的大小
      【注意】做页面的时候，一开始测量的是盒子的大小，但我们会直接设置成width、height。若之后才发现需要添加padding、border，盒子会被撑大。为了保证盒子大小不变，width、height需要减去对应的值。

##### （二）padding

​       1.padding取值:遵循上右下左原则，缺省的值找反义词的值
       2.padding-方位
     【注意】(1)padding不可以为负值;
                    (2)背景会从padding的区域左上角开始摆放，说明background-position:0 0;在padding区域的左上角

##### （三）margin

​       1.margin取值:遵循上右下左原则，缺省的值找反义词的值
        2.margin-方位
       【注意】margin可以为负值

### 六、元素类型

##### （一）块级元素

​     body、h1-h6、p、列表ul>li ol>li dl>dt+dd、form

​      特点： 

​	 (1)默认占一整行：即使设置了宽度，右边多余的部分也会用margin进行填充。
         (2) 可以设置宽高
         (3) 块级元素可以嵌套所有的行内元素以及部分的块级元素
         {错误： p>p  p>div  }
         (4)大部分的块级元素都拥有默认的margin或padding，除了div、li...

######          *应用场景： 怎么实现块级元素在父容器里水平居中？

​           答：给该块级元素添加｛margin:0 auto;｝

##### （二）行内元素

​	加粗、倾斜、a、span、img、input、textarea、label  

​        特点：

​	（1）一行显示多个
        （2）宽高由内容决定，不能设置宽高
        （3）行内元素也遵循盒模型，如可以定义padding,border,margin,background等属性，但个别属性不能正确显示如：padding-top/bottom;margin-top/bottom;)

######          *应用：行内元素如何实现在容器中水平居中呢？

​                 答：  给其父容器添加text-align:center;

###### 	 *应用 :行内元素如何实现在容器中垂直居中呢？

​		答：利用中线对齐{display：inline-block；vertical-align：middle；}对应的尺子高度为100%.

##### （三）元素类型的转换display

​      1. inline 转换成行内元素
      2. block 转换成块级元素
      3. list-item 转换成列表项 (li)......
      4. inline-block 转换成行内块级元素 
          特点：（1）一行显示多个  （2）可以设置宽高【当元素设置了float属性后，就相当于给该元素加了display:inline-block;】

      5. none 隐藏元素，不占位置      
    
      6. A、大部分块元素display属性值默认为block，其中列表li的默认值为list-item。
    
         B、大部分内联元素的display属性值默认为inline,其中img,input,textarea默认为inline-block。           

##### （四）行内块级元素与浮动的区别:

​      1.两个行内块级元素之间存在空格，会在页面中存在一条缝隙。浮动则不会。
           解决办法：

​		（1）将元素之间的空格删除
                （2）给其父元素设置｛font-size:0;｝
        2.行内元素都存在垂直方向基线对齐的问题
               	 解决办法: 设置vertical-align

```
.market_b{width: 1000px;height: 300px;border:1px solid #ccc;font-size:0;
/*font-size：0；解决行内块级元素之间存在缝隙的问题*/
	text-align:center;}
.market_b0{display:inline-block;
                    /*设置成行内块级元素，但两个行内块级元素之间会有一条缝隙，所以用font-size：0；解决*/
            width: 210px;height: 210px;background: red;margin-right:39px;}
        .last{margin-right:0;}
```



##### （五）如何实现元素在容器的垂直方向上居中

​      1.设置一把尺子｛width:0;height:父容器的高度｝
      2.该元素与尺子都设置｛display:inline-block;vertical-align:middle;｝

​      3、【具体操作】设置一个元素在一个容器中垂直居中，必须更改默认的display属性值为inline-block;并加上同级元素标尺（同级元素[标尺]样式设置为vertical-align:middle;width:0;height:100%（父容器的高度）;display:inline-block;）。

```
<style type="text/css">

    .bigbox{width: 600px;height: 600px;border:1px solid #ccc;}
    .bigbox .smallbox{display:inline-block;width: 150px;height: 150px;background: red;vertical-align: middle;}
    .bigbox .chizi{display:inline-block;width: 0px;height: 600px; vertical-align: middle; }
  </style>
```

```
<div class="bigbox">
        <div class="smallbox"></div>
        <div class="chizi"></div>
    </div>
```

### 七、定位+锚链接

##### （一）静态定位 position:static; 

​      position:static; 静态定位(默认标准流定位)
      无法设置left、right、top、bottom值

##### （二）相对定位position:relative；

​      (1)相对于自己本身所在的位置进行移动定位
      (2)配合left、right、top、bottom进行移动定位。相对于自己的某条边往元素中心移动为正值。
       (3)相对定位的元素不脱离标准流。（即使定位移动到其他位置，自己原来位置也不给别人用。）（灵魂出窍）

##### （三）绝对定位position:absolute; 

​       (1)绝对定位的元素是相对于html或者最近的有定位的父元素 进行定位
       (2)配合left、right、top、bottom进行移动定位。相对于包含块的某条边往包含块中心移动为正值
       (3)绝对定位的元素会脱离标准流

##### （四）如何用定位实现元素在容器中居中？

​        1.子绝父相（子元素用绝对定位，父元素用相对定位或是其他定位）

​	2.子元素{top:50%;margin-top:-自己高度的一般;left:50%;margin-left:-自己宽度的一半。}

##### （五）固定定位position:fixed ; 

​       (1) 相对于浏览器的可视区域进行移动定位
       (2) 配合left、right、top、bottom进行移动定位。相对于浏览器可视区域的某条边往浏览器可视区域中心移动为正值
       (3) 脱离标准流

##### （六）定位元素层叠属性（层级z-index）

​	1、z-index : auto |number   检索或设置对象的层叠顺序。auto：默认值。ber:无单位的整数值。num可为负数。没有设置z-index时，最后写的对象优先显示在上层，设置后，数值越大，层越靠上；

​	2、较大 数值的对象会覆盖在较小 数值的对象之上。如两个绝对定位对象的此属性具有同样的 number 值，那么将依据它们在HTML文档中声明的顺序层叠。

​	3、此属性仅仅作用于 position 属性值为 relative 或 absolute 的对象。

```
.dv1{        width:300px;height:300px;background-color: red;
            position:relative;top:100px;
            z-index:-100;
        }
        .dv2{width:300px;height:300px;background-color: blue;}
        
此时z-index作用在dv1上，为负值，所以dv2的蓝色块覆盖在dv1的蓝色块上。若改为正值，则红色块覆盖蓝色块。
```

##### （七）锚链接（命名锚点）

​        a[href="#id名"]跳转到id名所在的元素上
        a[href="页面路径#id名"]跳转到其他页面该id名所在的元素上

### 八、overflow

##### （一）overflow 内容溢出容器时的处理方式   

       1. 属性值：
    
          	（1）visible 默认值，其中的内容无论是否超出范围都将被显示。
    
          	（2） hidden 效果与visible相反。任何超出“width”和“height”的内容都会隐藏。
    
          	（3） scroll 无论内容是否超越范围，都将显示滚动条。 
    
          	（4）auto 当内容超出范围时，显示滚动条，否则不显示。
    
          2.设置某个方向： 
    
          	overflow-x 水平方向   overflow-y垂直方向
    
          规定：当某一个方向的值设置不为visible，另外一个方向会自动设置成auto

##### （二）简易轮播图

​	1、设置总的大盒子，再设置图片的盒子以及按钮的盒子放图片和按钮。用定位（子绝父相）把两个小盒子放进大盒子里。

​	2、要使图片跟着按钮变化，用锚链接：按钮a[href="# id名"]，图片设置对应的id名。

```
 <style type="text/css">
        .bigbox{width: 300px;height: 300px;border:1px solid #ccc;position:relative;}
        .bigbox .imgbox{width: 300px;height: 300px;background: red;overflow:hidden;
        /*图片溢出用overflow：hidden；
        }
        .bigbox .imgbox img{width: 300px;height: 300px;}
        .bigbox .btnbox{
            width: 120px;height: 20px;background: yellow;
            position:absolute;right: 0;bottom:0;
        }
        .bigbox .btnbox a{float:left;width: 20px;height: 20px;text-align: center;line-height: 20px;}
    </style>

<body>
    <div class="bigbox">
        <div class="imgbox">
            <img src="../images/13.jpg" id="img1" />
            <img src="../images/19.jpg" id="img2" />
        </div>
        <div class="btnbox">
            <a href="#img1">1</a>
            <a href="#img2">2</a>
        </div>
    </div>
```

##### （三）二级导航条

##### （四）阅读器

### 九、图片整合

##### （一）精灵图sprites

###### 1、概念

​	将导航背景图片、按钮背景图片等有规则的合并成一张背景图，即将多张图片合为一张整图，然后用background-position”来实现背景图片的定位技术。

###### 2、图片整合的优势

​	1）通过图片整合来减少对服务器的请求次数，从而提高页面的加载速度。

​	2）通过整合图片来减小图片的体积。

###### 3、精灵图的创建

​	1）在FW软件中  新建→画布→注意选择透明→导入小图标→制作精灵图

​	2）在html中用i标签放小图标。第一张图用background：url（）x y；其他图用background-position：x y；

##### （二）滑动门

​	1.通过多张背景图片进行层叠，从而在视觉上达到同一张图片的效果。

​	2.a{padding-left存放左边的背景图片}>span{padding-right以实现文本居中}【a{padding-left的值与span的padding-right的值相同】

```
	    .tab2 li{float: left;margin-right: 2px;}
        .tab2 li a{display: block;height: 42px;padding-left:4px;background:url("../images/left.gif") no-repeat;}
        /*a标签的padding对于span来说是margin,所以span的背景图片从右边开始摆放，不会影响到a标签padding内的背景图片*/
        .tab2 li  a span{display:block;height: 42px;background:url("../images/right.gif") right top;padding-right: 4px;}
```

```
<ul class="tab2">
        <li><a href="#"><span>你困了吗</span></a></li>
        <li><a href="#"><span>我还很清醒呢</span></a></li>
        <li><a href="#"><span>呵呵</span></a></li>
        <li><a href="#"><span>哈哈哈哈哈</span></a></li>
    </ul>
```

### 十、宽高自适应

###### 	通过子元素及窗口大小调整元素大小，从而达到适应不同设备、不同的分辨率。

##### （一）宽度自适应

​	当块级元素的宽度设置成100%，或者不设置，宽度默认都是占父级元素的100%。
        经验：当父元素脱离了标准流（浮动），且父元素不设置宽度，可以由子元素撑开它的宽度。

##### （二）高度自适应

###### 	1、父元素高度自适应

​	height:auto;或者不设置,都是由子元素撑开这个父元素的高度。        

###### 	2、元素高度自适应窗口高度设置方法

​	html,body{height:100%;}	 E{height:100%;}

​	注：如果设置子元素的高度跟随父元素的高度变化而变化，那么父元素必须有高度。

###### 	3、高度塌陷

​	当子元素都浮动了，父元素会没有子元素撑开高度。

  	  解决办法：
   	 （1）给父元素加overflow:hidden;（缺点：若存在内容溢出，会被裁剪掉。）
   	 （2）给父元素添加最后一个子元素（块级){height:0;clear:both;overflow:hidden;} 缺点：会产生很多多余的标签
   	 （3）伪元素清除法， .clearfix::after{ content:"";display:block;height:0;clear:both;overflow:hidden;visibility: hidden;}
      	  一般我们用的时候,我们只需要将【类名.clearfix】添加到父元素上即可（在父元素的class里面添加）。

###### 	4、最小高度 min-height

* 当内容高度小于最小高度，按最小高度显示；

* 当内容高度大于最小高度，按内容高度显示。
  应用场景：内容不确定，无法较好地控制父元素高度

  ###### 5、过滤器_height

  ​	兼容ie6： ie6中，height代表的是最小高度。若想这个属性只让ie6识别，通过过滤器_height。

##### （三）伪元素

######       1、E::before{content：“  ”} 

​	 给E元素添加第一个子元素,content:""不能省略（E元素必须是块级元素）
               *元素类型默认为行内元素
                *content:url();添加图片

###### 	2、E::after  

​	给E元素添加最后一个子元素

######       3、E::first-letter 

​	给E元素的第一个文本添加样式

######       4、E::first-line 

​	给E元素的第一行文本添加样式   

```
.box::before{content:url("../images/3.jpg"); }
.box::after{content:"作者：费玉清";}
.duanluo::first-letter{font-size: 100px;color:red;}
.duanluo::first-line{background-color: #ccc;}
```

### 十一、浏览器兼容

##### （一）隐藏元素的两种方式

 	1.display:none 隐藏元素，不占位置
        2. visibility:hidden; 隐藏元素，占位置

##### （二）图片有边框bug

​	图片有边框（ie8-） 

​	解决办法： 

​		img{border:0 none;}

##### （三）图片有间隙

​	div>img,img下方会存在间隙
        解决办法：
                * img{display:block;}
                * div{font-size:0;}

##### （四）双倍浮向问题

​	ie6-，会错误地将浮动元素的浮向边margin加倍显示。
        解决：   ｛display:inline;｝

##### （五）默认高度

​	ie7-，存在默认高度16px。
        解决办法:
               * {font-size:0;}
               *{overflow:hidden;}

##### （六）表单元素行高不一致的bug

​	表单元素行高不一致问题（基线对齐的问题）
         解决办法：
               * {vertical-align: middle;}
               * {float:left;}

##### （七）表单元素样式不一致

​	表单元素样式在各浏览器渲染效果不一
        解决办法：

​	给input清除默认样式{display:block;border: 0 none;padding:0;}，给input外层嵌套标签，设置input需要的样式

```
div{width: 200px;border:1px solid #ccc;}
        input{
            display:block;height: 40px;border: 0 none;padding:0;outline:none;
            line-height:40px;
        }

```

##### （八）百分比bug

​	浮动元素50%+50%>100% （ie6-）
        解决办法： 若两个元素都左浮动，给元素添加{clear:right;}

##### （九）鼠标指针

​	ie8及以下浏览器才支持cursor:hand;
        解决办法： ｛cursor:pointer;｝

##### （十）透明属性

​	透明度
                * opactity:val; val取值为0-1，越大越不透明。
                * filter:alpha(opacity=val)   val取值为0-100，整十数，越大越不透明。

##### （十一）margin塌陷

​            父元素与第一个子元素存在上间距，若给第一个子元素加margin-top，会错误地渲染成父元素的margin-top。
            解决办法： 
                    （1）子元素或者父元素浮动
                    （2）给父元素加overflow:hidden;
                    （3）给父元素加border-top
                    （4）将子元素的margin-top当作父元素的padding-top

##### （十二）margin合并

​	当两个块级元素竖直排列时，上一个元素的margin-bottom与下一个元素的margin-top会发生合并，它们之间的margin取两者之间较大的值。

​	防止margin合并：bfc内部布局与外部不相干。

​	.dvl(overflow:hidden;)>.sao(宽高背景margin-bttom)+.dv2(margin-top)

##### （十三）属于同一个 bfc 的两个相邻块会发生margin重叠

##### （十四）bfc的区域不会与浮动块重叠

##### （十五）计算bfc高度时，里面的浮动元素也参与计算

​	触发条件：html 、overflow不为visible、脱离标准流的定位、、float、display：inline-block/flex

##### （十六）自适应两栏布局

###### 	1、方法一： 左边定宽加浮动，右边margin-left留出左边的宽

​	（因为浮动的元素会脱离标准流，第二个元素会跑上来占据第一个元素的位置，而块级元素的宽度刚好是100%，当设置了margin-left为第一个元素的宽度，它的宽度会自动调整为页面剩余部分的宽度）

```
 /*.dv1{width: 200px;height:600px;background-color: red;float: left;}
        .dv2{margin-left:200px;height: 600px;background: blue;}*/
```

###### 	2、方法二：左边定宽加浮动，右边不定宽加overflow:hidden

​        原理：bfc的区域不会与浮动块重叠

##### （十七）防止margin重叠

/*属于同一个bfc的两个相邻块会发生margin重叠*/ 

### 十二、高级表单、表格

##### （一）新增表单标签

###### 	1、表单字段集fieldset

​	相当于一个方框，在字段集中可以包含文本和其他元素对表单中的元素进行分组，可以嵌套多个fieldset。

​	disabled可以定义在空间中禁止使用。

###### 	2、字段集标题legend

​	fieldset>legend字段集标题（必须作为表单字段集的第一个子元素）[align控制它在fieldset的某一个位置]。如：align=“center”在中间。

###### 	3、提示信息标签label

​	[for] 关联到id名所在的表单元素
        若用于单选框或多选框，一般都是直接将文字及表单元素包含在label里面。

​	要使文本框对齐，给label设置宽度。

###### 	4、type属性值

​	1.input[type="file"]上传文件 [multiple多选]
        2. input[type="image"] 图像提交按钮 [src图片路径]

##### （二）表格标签

###### 1、标题行单元格 th

​	默认加粗居中

######  2、 表格标题caption

​	作为table的第一个子元素

###### 3、行分组thead      tbody     tfoot  

1.thead表头     tbody表体      tfoot表尾
        thead>tr>th        

​	tbody>tr>td   

​	tfoot>tr>td
2.书写顺序：thead、tfoot、tbody，这样子保证在数据加载完毕前，先呈现表头跟表尾。
3.如果要使用 thead、tfoot 以及 tbody 元素，就必须使用全部的元素。(如果没有表尾，就省略tfoot)

###### 4、列分组colgroup

​	[span表示每个列分组占据的列数]

```
<colgroup span="2"></colgroup>
表示两列形成一个列分组
```

###### 5、table【rules】【align】

​        [rules 添加分隔线]:cols列分隔线   rows行分隔线   
        all 行与行、列与列都存在分隔线   none没有     groups组分隔线
        [align] 整个表格在其父元素的水平对齐方式

#####  （三）表格的css属性

######  	1、(table)border-spacing 

​		单元格与单元格之间的间距,不可取负值

######          2、(table)border-collapse 

​		合并单元格边框
                属性值：separate默认分离  collapse合并

######           3、(td)empty-cells 

​		无内容时单元格边框的设置
                 属性值：show默认出现   hide隐藏

######            4、(caption)caption-side

​		top/right/bottom/left
                left,right位置只有火狐识别

##### （四）html5新表单标签

​	1）拥有输入功能的下拉列表 input[list]+datalist[id]>option;
        2）输出output，配合着form[oninput]使用。

##### （五）新表单类型type

​	 1）color 拾色器
         2）email 邮箱（正则验证）
         3）number 数字
         4）tel 电话号码
          5）url 网址（正则验证）
          6）search 搜索
          7）range 特定范围内的数值选择器，min最小值、max最大值、step( 步数 )、value当前值

##### （六）表单html新属性

######             1.autofocus 自动聚焦

######             2.placeholder 占位符

######             3.required 必填项（定义一个表单元素不能为空）

######             4.pattern  正则

### 十三、HTML5新标签、新表单类型、video

##### （一）doctype生命文档类型

以下均为快捷方式：

​	<!-- doctype html声明文档类型为html5 -->
<!-- <!DOCTYPE html> -->


<!-- html:4t+tab ：声明文档类型为html4.01版本的过渡时期-->

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

##### （二）语义化标签

###### 	1、header头部标签 

​		一般都是包含标题标签或者导航条。header、footer不互相嵌套。

######         2、hgroup对标题进行组合 

######         3、footer 

​		一般都是版权信息、作者简介。。。

######         4、nav导航条

######         5、main主要内容  

​		主要内容，一个页面就用一次，外层结构。

######         6、article文章 

​		文章、独立的内容块。article可以嵌套自己。

######         7、section区块 

​		章节、区块，专题性的内容

######         8、aside侧边栏 

​		侧边栏，非正文的内容

###### 	9、figure对图片和文字进行组合

​		对图片跟文字进行组合>figcaption 对figure的内容进行说明

###### 	10、time时间

​		时间 [datetime 规定具体时间]

###### 	11、details细节

​		细节[open默认显示细节]>summary 对细节的总结

###### 12、mark标记

###### 	13、progress进度条

​		progress[max最大值]

​				[value当前值]

###### 	14、meter度量尺

​			[min最小值]

​			[max最大值]

​			[low较低的值]

​			[hieght较高的值]

​			[value当前值]

​			[optimum较佳的值，当取值小于较低的值说明越低越好，反之。]

###### 	15、ruby注释

​		注释标签>rt 对内容的注释信息；

###### 	16、video视频

​		引入视频的方式：video[src]或者video>source[src]

​		(1)[controls]控制条
    	    	(2)[autoplay]自动播放
        	(3)[loop]循环播放
        	(4)[width][height]
        	(5)[poster]等待加载时的图片

    支持格式：ogg、mp4、webM
    -->
    <!-- <video src="../images/movie.ogg" autoplay width="600" height="600"></video> -->


##### （三）语义化标签布局

```
<body>
    <header id="header"></header>
    <nav id="nav"></nav>
    <main id="main">
        <article class="main_l">
            <section class="section">
            </section>
        </article>
        <aside class="main_r"></aside>
    </main>
    <footer id="footer"></footer>
</body>
```

### 十四、css3选择器

#### 一、选择器

##### （一）基本选择器

###### 	1、标签（元素）选择器

​		通过标签名获取元素元素；

###### 	2、类选择器

​		通过 .类名获取元素；

###### 	3、id选择器

​		通过#id名获取元素；

###### 	4、通配符选择器

​		通过*获取页面中的所有元素；

###### 	5、群组选择器E1,E2

​		通过，获取到多个基本选择器如E1,E1中的相同样式。

##### （二）层次（关系）选择器

###### 	1、后代选择器：E1  E2

​		中间用空格隔开表示获取到的E2元素是E1元素的后代；

###### 	2、子代选择器：E1>E2 

​		表示获取的E2元素是E1元素的子代，子代仅仅表示下一代。（需注意，有些样式会继承。）

###### 	3、相邻兄弟选择器：E1+E2

​		表示获取到的E2元素与E1元素同级，并且E2元素紧跟在E1元素的后面（即E1元素的后面一个就是E2元素）；

###### 	4、兄弟选择器：E1~E2

​		表示获取到E1后面的所有E2元素。

##### （三）动态伪类选择器

###### 	1、：link

​		锚链接被访问前添加的样式；

###### 	2、：visited 

​		锚链接被访问后添加的样式；

###### 	3、：hover

​		鼠标悬停在任意元素上添加的样式；

###### 	4、：active 

​		鼠标点击任意元素时添加的样式；

###### 	5、：focus 

​		表单被聚焦时添加的样式。 

```
  <style type="text/css">
        a:link{color:#000;}
        a:visited{color:#ccc;}
        a:hover{color:#58bc58;}
        a:active{color:red;}
        input:focus{background: #000;}
    </style>
</head>
<body>
    <a href="#">喵喵</a>
    <input type="text" />
    <input type="password" />
</body>
```

##### （四）目标伪类选择器

​	锚点的目标元素被选中

```
/意味着：当h2是当前锚链接的目标时，就会向h2中添加样式/
h2:target{color: red;}

<ul class="nav">
   <li>CSS (层叠样式表)</li>
   <li>实例</li>
  </ul>
<div class="content">
   <h2 id="title1">CSS (层叠样式表)</h2>
```

##### （五）UI状态伪类选择器

###### 	1、：enable

​		 可用的表单元素添加样式

###### 	2、：disable

​		不可用的表单元素添加样式

###### 	3、：checked

​		选中的表单选框添加样式.    

##### （六） 结构伪类选择器

######             1、E：first-child

​		获取到其父元素的第一个子元素，且要满足为E元素

######             2、E:last-child

​		获取到其父元素的最后一个子元素，且要满足为E元素

######             3、E：nth-child(n)

​		获取到其父元素的第n个子元素，且要满足为E元素。从1开始计数。

###### 	   4、E:nth-last-child(n) 

​		获取到其父元素的倒数第n个子元素，且要满足为E元素。从1开始计数。
       【 * n的取值： 具体数值    odd（2n-1）第奇数个孩子   even（2n）第偶数个孩子   
                            -n+a 获取到父元素第一个到第a个孩子】

###### 	5、E:first-of-type 

​		获取到其父元素的第一个E类型的子元素

######          6、E:last-of-type

​		 获取到其父元素的最后一个E类型的子元素

###### 	7、E:nth-of-type(n)  

​		获取到其父元素的第n个E类型的子元素

###### 	8、E:nth-last-of-type(n)  

​		获取到其父元素的倒数第n个E类型的子元素

###### 	9、E:empty  

​		空文本的E元素（不能有空格）添加样式

###### 	10、E:only-child  

​		 获取到其父元素唯一的一个子元素,且要满足为E元素

```
/*.zhubaba div:only-child{background: red;}*/
```

###### 	11、E:only-of-type  

​	获取到父元素的唯一一个E类型的孩子

##### （七）否定伪类选择器

​	G（父元素）    F:not(E)  获取到G元素中除了E条件以外的所有F元素

##### （八）伪元素选择器

###### 	    1.E::before{content:""}

​		 给E元素添加第一个子元素（行内元素）

######             2.E::after{content:""} 

​		给E元素添加最后一个子元素

######             3.E::first-letter{content：""}

​		给元素的第一个文本添加样式

######             4.E::first-line{content:""}

​		给元素的第一行文本添加样式

######             5.E::selection 

​		E元素的内容被选中时添加样式
        兼容火狐::-moz-selection

##### （九）属性选择器

​    E[attr] 拥有该attr属性的E元素被获取到（attr---属性）

######     1、 E[attr="val"]等于

​	 拥有该attr属性，且属性值等于val值的E元素被获取到

######     2、E[attr*="val"] 包含

​	拥有该attr属性，且属性值包含val值的E元素被获取到

######     3、E[attr^="val"] 开头

​	拥有该attr属性，且属性值以val值开头的E元素被获取到		          

######      4、E[attr$="val"]结尾

​	 拥有该attr属性，且属性值以val值结尾的E元素被获取到

```
		input[value]{background: red;}
        input[type="text"]{color:orange;}
        input[value*="bc"]{font-size: 40px;}
        input[value^="ab"]{font-style:italic;}
        input[value$="e"]{font-size:50px;}
```



##### （十）语言伪类选择器

​	q:lang(no){quotes:"""";}
        q[lang="no"]在内容两侧会生成引号，若想改变符号，通过如上的语言伪类选择器

#### 二、文本属性

##### （一）文本阴影 text-shadow

​	    总属性：x-offset  y-offset blur color[,...];
            x-offset 水平偏移，往右为正
            y-offset 垂直偏移，往下为正
            blur 模糊区域，不能取负值

##### （二）文本溢出 text-overflow

​             属性值： clip默认不处理   ellipsis 以省略号的形式出现
             配合三个属性使用：width、white-space:nowrap、overflow:hidden

##### （三）单词换行 word-wrap

​	    word-wrap:break-word;

##### （四）自定义字体 @font-face

​	 @font-face{font-family起名字;src:url("字体路径")}

##### （五）字体图标*

#### 三、背景属性

##### （一）背景图片的尺寸 background-size

​      取值：

######          1、数值

​		 水平 垂直; 绝大部分情况会出现扭曲变形。

######           2、cover 

​		背景图片完全覆盖容器,绝大部分会出现背景图丢失一部分的情况

######           3、contain 

​		容器完全包含背景图片,绝大部分会出现容器留白现象
             等比缩放：cover、contain
             应用：一般轮播图采用背景图片｛background-size:cover;background-position:center center;｝

##### （二）背景图片的定位区域 background-origin

​       属性值：
             默认从padding开始摆放 padding-box
             从content开始  content-box（说明此时background-position:0 0;在content内容的左上角。）
              border-box 

```
background: url("../images/24.jpeg") no-repeat;
background-origin:border-box;
```


     /*background-position背景图片在容器的定位区域中的位置*/
##### （三）背景图片的裁剪background-clip

​		（最终显示区域）

​             border-box 从边框部分开始裁剪
             padding-box 从padding部分开始裁剪
             content-box 从content部分开始裁剪

##### （四）多张背景图片的摆放

```
div{
            width: 600px;
            height:600px;
            border:1px solid #ccc;
            background:
                url("../images/01.jpg") no-repeat left top ,
                url("../images/02.jpg") no-repeat center top ,
                url("../images/03.jpg") no-repeat right top ,
                url("../images/04.jpg") no-repeat left center ,
                url("../images/05.jpg") no-repeat center center ,
                url("../images/06.jpg") no-repeat right center ,
                url("../images/07.jpg") no-repeat left bottom ,
                url("../images/08.jpg") no-repeat center bottom ,
                url("../images/09.jpg") no-repeat right bottom;
            background-size:200px 200px;

        }
```

### 十五、边框属性、渐变、过渡、2d变换

##### （一）边框属性

######         1、边框阴影box-shadow

​	    总属性：x-offset y-offset blur spread color inset[,...];
            x-offset 水平偏移，往右为正值
            y-offset 垂直偏移，往下为正值
            blur 模糊区域
            spread 扩展区域
            color 颜色
            inset 往元素内部移动。若是不设置，则往元素外部添加边框阴影

###### 	2、边框图片 border-image

​            边框图片引入border-image-source:url()
            边框图片的裁剪 border-image-slice 遵循上右下左原则(不带单位)
            边框图片的宽度 border-image-width 若省略该值，默认就是边框宽度
            边框图片的重复 border-image-repeat
            属性值：stretch默认拉伸    repeat重复  round压缩重复
            边框图片向外延伸 border-image-outset 不能取负数

###### 	3、边框圆角 border-radius

​            某个角的边框圆角：border-垂直方位-水平方位-radius:水平半径 垂直半径;
             border-radius:水平半径/垂直半径;
             水平或垂直半径遵循（从左上角开始）顺时针原则,缺省的值找对角

##### （二）渐变

######         	1、线性渐变  linear-gradient

​                1.gradient(linear,起点坐标,终点坐标,from(color),to(color))
                    坐标写法：水平坐标 垂直坐标; (只能用百分比)
                2.gradient(linear,起点坐标,终点坐标,color-stop(渐变开始的位置,color)[,...])
                    渐变开始的位置取值为0-1
                3.linear-gradient(方向||角度,颜色 渐变开始的位置)
                    方向：top bottom left right
                    角度单位:deg
                    渐变开始的位置:0-100%
                    老版本（加前缀的写法）+新版本 = 90deg

###### 		2、径向渐变radial-gradient

​               radial-gradient(圆心，颜色 开始渐变的位置[,....])
               radial-gradient(圆心,size||shape,颜色 开始渐变的位置[,....])
               size大小：
                        closest-side：最近边； 
                        farthest-side：最远边；
                        closest-corner：最近角；
                        farthest-corner：最远角（默认值）
                shape形状：
                        ellipse椭圆形(默认)，circle表示圆形。

###### 		3、 重复渐变 repeating-linear（radial）-gradient 

​		用法同上

##### （三）浏览器的私有前缀

| 浏览器        | 内核    | 私有前缀 |
| ------------- | ------- | -------- |
| chrome/safari | Webkit  | -webkit- |
| Opera         | Presto  | -o-      |
| ie            | Trident | -ms-     |
| firefox       | Gecko   | -moz-    |
| chrome/opera  | blink   | 暂无     |

##### （四）过渡 transition

​	过渡：让变化在一段时间内进行

​            1. 需要过渡的属性  transition-property
            2. 过渡的时间 transition-duration
            3. 过渡的形式 transition-timing-function
                *linear 匀速    ease慢速进入慢速离开
                *ease-in 慢速进入   ease-out慢速离开
                *ease-in-out慢速进入慢速离开
            4. 过渡的延迟 transition-delay
            5.总属性 transition: 1 2 3 4;(1跟2不可以省略)
            多个属性同时过渡可以用all。

案例：360案例、泡泡案例等。

##### （五）2d变换transform 

​		==>这是一种状态

###### 	1、移动变换 transform:translate

​		(水平方向(右),垂直方向(下))
                改变某个方向 transform:translateX(水平方向) 
                transform:translateY(垂直方向)
                取值取百分比的话，指的是参考自己的宽高

​		应用：

​		（1）利用移动变换实现小盒子在大盒子居中：子绝父相，left50%，top50%，transform:translate(-50%,-50%)；

​		（2）盒模型的取值写百分比，指的是父元素宽高的百分比：content（width、height）、border、padding、margin

###### 	2、缩放变换transform:scale(x,y)

​            取值为缩放比（倍数），基准点为元素中心。
            transform:scaleX(x)    transform:scaleY(y)

###### 	3、旋转变换 transform:rotate(deg)

​            顺时针旋转为正值，基准点在元素中心

###### 	4、扭曲变换transform:skew(x轴旋转的角度，y轴旋转的角度)

​           transform:skewX(x轴旋转的角度)

###### 	5、改变元素变换的基准点 transform-origin

​                取值：数值 百分比 方位

```
            /*transform-origin 改变基准点*/
            transform-origin:left top;
```



###### 	6、注意：先移动，在旋转。

### 十六、盒模型、3d变换、关键帧动画

##### 	(一)颜色模式

​	（为属性值：可以控制某个属性）

######             1、rgba

​		(red0-255,green0-255,blue0-255,alpha不透明度0-1)

######             2、hsla

​		(色调0-360,饱和度0-100%,亮度0-100%,alpha0-1)

######             3、transparent 

​		完全透明 (三角形)

​		

```
 div{
            width: 0;height: 0;
            border-left:10px solid transparent;
            border-right:10px solid transparent;
            border-top:10px solid green;
        }
```

##### (二)盒模型

​        盒模型由content内容、padding内填充、border边框、margin外间距组成。

######         1、标准盒模型content-box（默认）

​		width、height指的是content的宽高

######         2、怪异盒模型: border-box

​		width、height指的是content+padding+border的宽高

######         3、box-sizing 规定盒模型

​            *属性值：content-box（默认）     border-box设置成怪异盒模型

##### （三）3d变换

######         1、移动变换transform:translate3d(x,y,z); 

​           transform:translateZ(z),其他方向同

###### 	2、保持3d变换transform-style:preserve-3d; （父元素上）

​                *flat平面（默认）

###### 	3、设置观察的距离，景深perspective(父元素上)

```
 perspective:10px;
 /*perspective-origin 改变观察的基准点*/
 perspective-origin:-200px -200px;
```

###### 	4.旋转变换transform:rotate3d(x,y,z,deg)；   

​                左手定律：大拇指指向轴的正方向，其他手指卷曲的方向为旋转的正方向
                transform:rotate3d(x,y,z,deg)  x、y、z取值为0（不旋转）或1（旋转）
                transform:rotateX(deg);

##### （四）案例

###### 1、立方体

​	1.先把所有的面都定位在盒子的同一位置

​	2.设置3d变换，将每个面移动到指定位置

​	3.设置景深

###### 2、3d导航

​	1.导航的套路
       	2.两个a一开始先放在li同一位置再进行移动旋转变换
       	3.hover之后整个li翻转即可。过渡及延迟。

##### （五）关键帧动画

######         1、自定义动画 

​        （1）通过@keyframes指定动画序列；@keyframes name{}
        （2）通过百分比将动画序列分割成多个节点；
        （3）在各节点中分别定义各属性
        （4）通过animation将动画应用于相应元素；

      （5）   @keyframes name{
                百分比{
                    声明
                }
            }
###### 	2、animation属性

​	总属性：animation:name duration  function  delay  count  direction  fill-mode;

​			（1,2不可缺省）

​	说明：

​		animation-name:动画名字

​		animation-duration:动画时间

​		animation-timing-function:动画形式（linear匀速播放）（steps一步一步改变）

​		animation-delay:动画开始之前的延迟

​		animation-iteration-count:动画播放次数（infinite---无限次播放）

​		animation-direction:动画播放方向

​			nomal（默认值）

​			reverse（动画反向播放）

​			alternate（动画在奇数次正向播放，在偶数次反向播放）

​			alternate（动画在奇数次反向播放，在偶数次正向播放）

​		animation-fill-mode:动画完成是应用的样式

​			none:默认

​			forwards:动画完成时保持最后的状态（在动画的最后一帧定义）

​			backwards:在动画显示之前（在动画第一帧中定义）

​			both:向前和向后填充模式都被应用

​		补充：animation-play-state:paused; 暂停动画

​	steps(n)、steps(n,end)每一帧都分成n步，每一步都以前一步的状态填充时间段（默认）
        steps(n,start)每一帧都分成n步，每一步都以后一步的状态填充时间段

### 十七、弹性盒布局、媒体查询

####  一、弹性盒布局

有能力规定其子项目的宽高在容器内进行扩展或伸缩，以确保子项目不会溢出容器。

##### （一）设置在父元素上

######          1、display:flex;

​	 将父元素设置成弹性盒，那么里面的子元素会在主轴方向上默认不换行摆放；侧轴方向的大小不设置的话，就会在当前行默认被拉伸

###### 	2、flex-direction 设置主轴方向

​                    属性值：
                        row 从左往右
                        row-reverse 从右往左
                        column 从上到下
                        column-reverse 从下到上

###### 	3、flex-wrap 伸缩换行

​                    *nowrap默认不换行
                    *wrap 换行
                    *wrap-reverse 换行反向    主轴是水平时，上下反向，主轴垂直时，左右反向；

###### 	4、flex-flow:flex-direction ||  flex-wrap;伸缩方向及换行

###### 	5、justify-content 设置子项目在主轴方向的对齐方式

​                flex-start 默认在主轴的起点位置靠齐摆放
                flex-end 在主轴的终点位置靠齐摆放
                center 在主轴的中间位置靠齐摆放
                space-between 将主轴方向空白区域平分在子项目之间
                space-around 将主轴方向空白区域环绕在子项目两侧

###### 	6、align-items 设置子项目在侧轴方向的对齐方式（当前行）

​                stretch 若不设置子项目在侧轴方向的大小，会被默认拉伸
                flex-start 若设置子项目在侧轴方向的大小，会被默认摆放在侧轴的起点位置
                flex-end 摆放在侧轴的终点位置
                center 摆放在侧轴的中间位置
               	baseline 子项目以基线对齐

###### 	7、align-content 控制子项目在侧轴方向的对齐方式（换行）

​                属性值等同于 justify-content

​		flex-start 默认在侧轴的起点位置靠齐摆放
                flex-end 在侧轴的终点位置靠齐摆放
                center 在侧轴的中间位置靠齐摆放
                space-between 将侧轴方向空白区域平分在子项目之间
                space-around 将侧轴方向空白区域环绕在子项目两侧

##### （二）设置在子元素上

###### 	1、flex设置子项目在主轴方向的比份

###### 	2、align-self设置单个子项目在侧轴方向的对齐方式（当前行）

​		stretch 若不设置子项目在侧轴方向的大小，会被默认拉伸
                flex-start 若设置子项目在侧轴方向的大小，会被默认摆放在侧轴的起点位置
                flex-end 摆放在侧轴的终点位置
                center 摆放在侧轴的中间位置
               	baseline 子项目以基线对齐

###### 	3、order 设置子项目的显示顺序

​		设置了order会放在没有设置order的子项目后面

​		都设置了order，数字越小的越靠前

案例：骰子案例；

#### 二、多列布局

###### 	    1、column-width 每列的最小宽度

######             2、column-count 最多的列数

######             3、column-gap 列间距

######             4、column-rule 列边框

######             5、column-span 跨列

​                *none不跨列 all跨所有列

#### 三、媒体查询

###### 	1、用法 @media screen and (条件){选择器{声明}}

​    	2、 min-width 当页面宽度大于最小宽度，生效。（从小写到大）
        	max-width 当页面宽度小于最大宽度，生效。（从大写到小）
        	min-device-width 【设备宽度】

###### 	3、link[media="screen and(条件)"][ href

```
div{
            width: 300px;
            height: 300px;
            background: blue;
        }
        /*当页面宽度w大于768px时，div显示红色。w<768,pink。w>992px,green。w>1200,blue。*/
        
        @media screen and (max-device-width:1200px){
            div{background:green;}
        }
        @media screen and (max-device-width:992px){
            div{background:red;}
        }
       
        @media screen and (max-device-width:768px){
            div{background:pink;}
        }
```

###### 	4、调用不同的css文件实现媒体查询

```
<link rel="stylesheet" media="screen and (max-width:1200px)" 		type="text/css" href="../css/a_1200.css" />

<link rel="stylesheet" media="screen and (max-width:992px)" type="text/css" href="../css/a_992.css" />
```

###### 	5、三种viewpoint视口

​	布局视口：以屏幕分辨率为基准，实际上布局视口的宽度要比屏幕宽出很多。

​	视觉视口：用户看到的网站展示区域，一般视觉视口和设备宽度一致。并且它的CSS像素的数量会随着用户缩放而改变。

​	理想视口：为了使网站在移动端有最理想的浏览和阅读宽度而设定。需要手动添写meta视口标签，一般视口大小都设置为设备大小。(快捷键---meta:vp)

#### 	四、布局

##### 	（一）自适应布局

​        元素的宽高自适应窗口或者子元素的大小，从而实现同一套页面适应不同的窗口、分辨率及设备。（！！！）

#####         （二）响应式布局

​	（一般都是用于较为简单的页面）
        响应不同的屏幕大小或者设备大小，对同一套页面的部分布局进行修改，但大体保持一致。

##### （三）移动页面布局	

​	1、meta:vp 设置理想视口
    	2. 观察设计稿640px-iphone5开发320px
        设计稿750px-iphone6开发375px
    	3. js代码的后三句复制过来，记得给meta加id名！！！！
    	4. #football{height:100%;display:flex;flex-direction:column;}
   	 除了main以外每一层都设置高度，main{flex:1;overflow-x:hidden;}
  	  !!!不要给main设置弹性盒



/*=============移动端步骤===================*/
/*
1.html，body{height：100%；}
2.#zhifubao{height: 100%;display:flex;flex-direction: column;}
3.其他版块都设置高，main{flex：1；overflow-x：hidden；}
 4.遇到多个方框组成的操作如下：
#main .main_t ul{display:flex;flex-wrap: wrap;text-align: center;}
#main .main_t ul li{
        width: 25%;height: 179px;
        border-right:1px solid #ccc;border-bottom:1px solid #ccc;
        display:flex;flex-direction: column;justify-content:center;
        font-size:26px;
        }
5.一般做footer时操作如下：
#footer{height: 90px;border-top:1px solid #ccc;}
#footer ul{display:flex;justify-content: space-between;padding:0 70px;text-align:center;font-size: 20px;}
#footer li{display:flex;flex-direction: column;justify-content: center;}
#footer li i{font-size: 40px;}

6.背景图片：将主轴方向改成垂直方向，再居中
#banner{height: 302px;display:flex;flex-direction:column;justify-content: center;background:url("../images/bank_banner.png");background-size:cover;background-position:center center;}

若颜色等改变，一般用类名改变：
#footer ul li.active{color:#00AAEE;}
 */