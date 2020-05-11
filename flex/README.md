> [转载自掘金-flex语法篇](https://juejin.im/post/5d5d0008f265da03a1485d4e)
> | [可参考-flex布局换行空白间隙之align-content](https://blog.csdn.net/txfyteen/article/details/82663029)


> Flexible Box 的缩写，即弹性布局。

> 注意：当设为flex布局之后，子元素的 `float` , `clear` , `vertical-align` 属性将失效。

> 注意：当父元素设为flex布局之后，自身是块级元素，如果需要变成行内元素可以使用 `inline-flex`。所有的子元素都会变成行内元素，如div等块级元素都会变成行内元素，可以在父元素中设置 `flex-direction: column`。

```css
/* 任何一个容器都可以指定为Flex布局 */
.box {
    display: flex;
}

/* 行内元素也可以使用flex布局 */
.box {
    display: flex;
}

/* webkit内核的浏览器，必须加上 -webkit 前缀 */
.box {
    display: -webkit-flex;
    display： flex;
}
```


---

###快速查找

#### 容器属性(父元素的属性)
[flex-direction](#flex-direction)： 决定排列方向

[flex-wrap](#flex-wrap)： 决定一行放不下的项目如何换行

[justify-content](#justify-content)： 定义项目在主轴上(水平方向)的对齐方式 

[align-items](#align-items)： 当只有一行项目在交叉轴(纵轴)上如何对齐 

[align-content](#align-content)：有多行项目时，在纵轴上的对齐方式


#### 项目属性(子元素的属性， 子元素>=1个)
[order](#order)： 定义项目的排列顺序。数值越小，排列越靠前，默认为0。 

[flex-grow](#flex-grow)： 定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

[flex-shrink](#flex-shrink)： 定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。


[flex-basis](#flex-basis)： 项目占据的主轴空间，浏览器根据这个属性，计算主轴是否有多余空间，默认为auto。当设置固定值，将占据固定空间。

[flex](#flex)： 是 flex-grow,flex-shrink, flex-basis的简写。默认为 0 1 auto,后两个属性可选。

[align-self](#align-self)： 允许单个项目与其他项目有不一样的对齐方式，可覆盖align-items属性，默认为auto


-------


### 设置容器属性
- <span id="flex-direction"> `flex-direction`： 决定排列方向
![image](https://user-gold-cdn.xitu.io/2019/8/21/16cb347f495812d3?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
```css
.box { flex-direction: column-reverse | column | row | row-reverse }

/* column-reverse: 主轴为垂直方向，起点在下沿
// column： 主轴为垂直方向，起点在上沿
// row(默认值)： 主轴为水平方向，起点在左端
// row-reverse: 主轴为水平方向，起点在右端。
/*
```

- <span id="flex-wrap"> `flex-wrap`： 决定一行排不了的项目如何让换行
```css
.box { flex-wrap: nowrap | wrap | wrap-reverse }

/* nowrap(默认): 不换行
// wrap： 换行，第一行在上面
// wrap-reverse： 换行，第一行在下面
*/
```
- <span id="flex-flow"> `flex-flow`: 是`flex-direction`和`flex-wrap`属性的简写
```css
.box {
  flex-flow: <flex-direction> || <flex-wrap>;
}
```
- <span id="justify-content"> `justify-content`： 定义项目在主轴上(水平方向)的对齐方式
![image](https://user-gold-cdn.xitu.io/2019/8/21/16cb34825804fd97?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

```css
.box { justify-content: flex-start | flex-end | center | space-between | space-around }

/* flex-start（默认值）： 左对齐
// flex-end: 右对齐
// center： 居中
// space-between： 两端对齐，项目之间的间隔都相等
// space-around： 每个项目两侧的间隔相等，所以，项目之间的间隔比项目与边框的间隔大一倍。
*/

```

- <span id="align-items"> align-items: 在交叉轴(纵轴)上如何对齐
![image](https://user-gold-cdn.xitu.io/2019/8/21/16cb348057dac34f?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
```css
.box { align-items: flex-start | flex-end | center | baseline | stretch }

/* flex-start：交叉轴的起点对齐。
// flex-end：交叉轴的终点对齐。
// center：交叉轴的中点对齐。
// baseline: 项目的第一行文字的基线对齐。
// stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
*/
```

- <span id="align-content"> `align-content`: 定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
![image](https://user-gold-cdn.xitu.io/2019/8/21/16cb34801db68176?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

```css
.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}

/* flex-start：与交叉轴的起点对齐。
// flex-end：与交叉轴的终点对齐。
// center：与交叉轴的中点对齐。
// space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
// space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
// stretch（默认值）：轴线占满整个交叉轴。
*/
```

### 设置项目属性
- <span id="order"> `order`: 定义项目的排列顺序。数值越小，排列越靠前，默认为0。
![image](https://user-gold-cdn.xitu.io/2019/8/21/16cb34804b32eebe?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
```css
.item {
  order: <integer>; // 整数
}
```

- <span id="flex-grow">  `flex-grow`： 定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。
```css
.item {
  flex-grow: <number>; /* default 0 */
}
```
![image](https://user-gold-cdn.xitu.io/2019/8/21/16cb34807deb93b5?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
如果所有项目的flex-grow为1，则它们将等分剩余空间。如果有一个flex-grow为2，其他为1，则前者占据的剩余空间比其他项多一倍。

- <span id="flex-shrink"> `flex-shrink`: 定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。
```css
.item {
  flex-shrink: <number>; /* default 1 */
}
```
![image](https://user-gold-cdn.xitu.io/2019/8/21/16cb3481436d7124?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
如果所有项目的flex-shrink都为1，当空间不足时，都将等比例缩小，如果一个项目的flex-shrink属性为0，其他项目为1，则当空间不足时，前者不缩小。

- <span id="flex-basis"> `flex-basis`： 项目占据的主轴空间，浏览器根据这个属性，计算主轴是否有多余空间，默认为auto。当设置固定值，将占据固定空间。
```css
.item {
  flex-basis: <length> | auto; /* default auto */
}
```

- <span id="flex"> `flex`： 是 `flex-grow`,`flex-shrink`, `flex-basis`的简写。默认为 `0 1 auto`,后两个属性可选。
```css
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}

/* auto---> 1 1 auto */
/* none---> 0 0 auto */
```

- <span id="align-self"> `align-self`: 允许单个项目与其他项目有不一样的对齐方式，可覆盖`align-items`属性，默认为auto
```css
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}

/* flex-start：交叉轴的起点对齐。
// flex-end：交叉轴的终点对齐。
// center：交叉轴的中点对齐。
// baseline: 项目的第一行文字的基线对齐。
// stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
// auto
*/
```
![image](https://user-gold-cdn.xitu.io/2019/8/21/16cb34812dab3110?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)