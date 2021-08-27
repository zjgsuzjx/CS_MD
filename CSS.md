> 💥此MD/PDF/HTML文档由 [@竹梦者也]([竹梦者也 - ZJXのBLOG (zjgsuzjx.top)](https://www.zjgsuzjx.top/)) 编辑制作，不可转载❌、打印❌、二次编辑❌、贩卖❌。仅供学习交流使用，下载后切勿随意传播。
>
> 📌欢迎在留言区提供修改建议~
>
> 
>
> ✅2021.6.22	 @竹梦者也(https://www.zjgsuzjx.top) 



## 一、CSS第一天

### 一、CSS简介

美化网页，而html只关注内容。是层叠样式表的简称，也是一种标记语言，也称为CSS样式表或级联样式表。主要设置网页的布局。最大价值：使结构（HTML）和样式（CSS）相分离。

#### 1. CSS语法规范

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/51150503993404c8e7f4b5bb9dd81e9d.png)

如：

```css
<style>
  p{
    color: #ff0000;
    front-size:12px;
  }
</style>
```

#### 2. CSS代码风格

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/4ce7e27447ab92a7b59b10fedfe3a228.png)

提倡展开格式，因为更加直观。

样式的大小写：提倡小写形式。

空格规范：在冒号后面有一个空格；在选择器和大括号中间也保留空格。

### 二、CSS基础选择器

#### 1. 选择器作用

选择标签用的。根据需求不同把不同的标签选出来。

#### 2. 选择器分类

可以分为基础选择器和复合选择器。

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/5823be06db76a02e79590ddca4e63c99.png)

#### 3. 标签选择器

是指用HTML标签名称作为选择器，按标签名称分类，为页面中<u>某一类标签指定统一的CSS样式</u>。

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/43b4f24b1ca022b59392ec4b5da1ec0a.png)

#### 4. 类选择器

差异化选择不同的标签，单独选一个或某几个标签。

```html
<head>
  <style>
    .p1 {
      color: #ff0000;
    }
  </style>
</head>
<body>
  <p class="p1">hello,world!</p>
  <p class="p2">hello,world!</p>
</body>
```

> 口诀：样式点定义，结构类调用，一个或多个，开发最常用

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/18f9c2748bedd1276a0cc8e5f17e6c33.png)

举个栗子：

```css
<head>
  <style>
    .d1 {
      width: 100px;
      height: 100px;
      background-color: red;
    }
    .d2 {
      width: 100px;
      height: 100px;
      background-color: green;
    }
  </style>
</head>
<body>
  <div class="d1"></div>
  <div class="d2"></div>
  <div class="d1"></div>
</body>
```

**类选择器-多类名：**可以给一个标签指定多个类名。多个类名要用空格分开。

如：

```css
<style>
  .d1 {
    color: red;
  }
  .d2 {
    font-size: 35px;
  }
</style>
<div class="d1 d2">刘德华</div>
```

**使用场景：**把公共的样式放到同一个地方。

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/e9308e28955677c74b43a914c6880287.png)

#### 5. id选择器

CSS中用#来定义，结构中用id调用。只能调用一次，别人切勿使用。

如：

```css
#d1 {
  color: red;
}
<div id="d1">刘德华</div>
```

id选择器和类选择器的**区别**：

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/a6347f259ac82b3125ea4a76c8e2cfe0.png)

#### 6. 通配符选择器

使用*定义，把html里所有的标签全部统一修改。

如：

```css
* {
  color: red;
}
```

#### 7. 基础选择器总结

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/0bc6be359994bfaa1de9025fb2c9e582.png)

### 三、CSS字体属性

#### 1. 字体系列

用front-family

如：

```css
h2 {
  font-family: '微软雅黑',Arial;
}
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/996a77c479a722437e2b746b9b401c7e.png)

> 如果有多个字体，会依次判断该电脑是否有这个字体。都没有的话会用浏览器自带的字体。

#### 2. 字体大小

用font-size，单位是px。

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/400dfd814b223609afea17213e501ca4.png)

> 标题标签比较特殊，需要单独指定文字大小。

#### 3. 字体粗细

用font-weight，可以用数字不带单位。

如：

```css
.p1 {
  font-weight: bold;
}
<p class="p1">hello</p>
```

实际开发中更多用数字。

#### 4. 文字样式

指文本风格，如斜体。

```css
.p1 {
  font-style: italic;
}
<p class="p1">hello</p>
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/8aea33f3d52d2215d3cba0c99ba29316.png)

#### 5. 字体复合属性

用来节约代码，有严格顺序要求。

```css
.p1 {
  /*font:font-style   font-weight  font-size/line-height  font-family*/
  font:italic 700 16px 'Microsoft YaHei';
}
```

**注意：**

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/2293cd3a821a093811ec6d4d3fce9fa3.png)

#### 6. 总结

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/756c8bab3c2cb49cb69902d8a4c65c93.png)

### 四、CSS文本属性

#### 1. 文本颜色

**有三种表示方法**：

1.red 

2.#ff0000

3.rgb(255,0,0或rgb(100%,0%,0%)

> 十六进制用的最多。

#### 2. 对齐文本

```css
.p1 {
  text-align: center;
  text-align: right;
}
```

默认值是left，即左对齐；本质是让盒子里的文字居中。

#### 3. 装饰文本

如下划线、删除线、上划线等。

```css
.p1 {
  text-decoration: underline;
}
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/1c835b5feec0d9790f736aa0205df4a0.png)

```css
a {
  text-decoration: none;
}
<a href="http://www.baidu.com">百度</a>
```

> 这个代码用的比较多，去掉链接的下划线。

#### 4. 文本缩进

给文本的第一行缩进

```css
p {
  text-indent: 20px;
}
```

**em**是一个相对单位，是当前文字一个文字的大小。

#### 5. 行间距

控制行于行之间的距离。

```css
p {
  line-height: 26px;
}
```

文本的行间距由三部分组成：

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/3f81b482f705b0e71a14d069770fe90f.png)

#### 5. 总结

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/8033f2344abf59d22c5aad476f652fea.png)

### 五、CSS引入方式

根据样式书写位置不同，可以分成三大类。

#### 1. 内部样式表

写在了htnl页面内部。就是单独放在style里，可以放在任何地方。

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/2c76230cc4217fa7dd052e3151adf8dd.png)

#### 2. 行内样式表

修改简单样式时使用。

如：

```css
<div style="color: red; font-size: 12px">DEMO</div>
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/cbedbf0ec0c85dece4f80cc17e028158.png)

#### 3. 外部样式表

适合样式比较多的情况。单独写到css文件中，之后将CSS文件引入到HTML文件中。

```css
<link rel="stylesheet" href="../css/1-3.css">
```

快捷键：输入link+Tab

> 这是最常用的方式。

#### 4. 总结

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/100feafabccd16bd5304ab7f280efd2f.png)

> 注意：给图片加不了居中对齐，必须给它的父亲<p>标签对齐。

### 六、Chrome调试工具

F12或右键审查元素->elements

① Ctrl+滚轮 可以放大开发者工具代码大小。

② 左边是 HTML 元素结构，右边是 CSS 样式。

③ 右边 CSS 样式可以改动数值（左右箭头或者直接输入）和查看颜色。

④ Ctrl + 0 复原浏览器大小。

⑤ 如果点击元素，发现右侧没有样式引入，极有可能是类名或者样式引入错误。

⑥ 如果有样式，但是样式前面有黄色叹号提示，则是样式属性书写错误。

## 二、CSS第二天

### 一、Emmet语法

用来提升CSS/HTML编写速度。

#### 1. HTML快速生成语法结构

1. 生成标签直接输入标签名 按tab键即可。比如 div 然后tab 键，就可以生成 

2. 如果想要生成多个相同标签 加上 * 就可以了 比如 div*3 就可以快速生成3个div 
3. 如果有父子级关系的标签，可以用 > 比如 ul > li就可以了 
4. 如果有兄弟关系的标签，用 + 就可以了 比如 div+p  
5. 如果生成带有类名或者id名字的，直接写 .demo 或者 #two tab 键就可以了
6. 如果生成的div 类名是有顺序的， 可以用 自增符号 $
7. 如果想要在生成的标签内部写内容可以用 { } 表示

```html
div{$}*5
=>
<div>1</div>
<div>2</div>
<div>3</div>
<div>4</div>
<div>5</div>
```

#### 2. CSS快速生成语法结构

1. 比如 w200 按tab 可以 生成 width: 200px; 
2. 比如 lh26px 按tab 可以生成 line-height: 26px

> 首字母+数学再按Tab



#### 3. 快速格式化代码

也就是快速对齐。可以使用快捷键。

> Vscode 快速格式化代码: shift+alt+f 

也可以设置 当我们 保存页面的时候自动格式化代码: 

1）文件 ------.>【首选项】---------->【设置】； 

2）搜索emmet.include; 

3）在settings.json下的【工作区设置】中添加以下语句：

"editor.formatOnType": true, 

"editor.formatOnSave": true

### 二、复合选择器

#### 1. 概念

建立在基础选择器之上，对基本选择器进行组合形成的。

可以更准确、更高效的选择目标元素。

由两个及以上基础选择器用不同方式合成。

> 总的来说，有class就用.类名，没有class就用标签名。

#### 2. 后代选择器

又称包含选择器，可以选择父元素里面的子元素。

```
//可以多层寻嵌套
ol li a {
  color: red;
}
```

要求如下：

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/3f46b701680dfdbf72a5e9a6d82061e0.png)

```css
//父类定义class为nav
.nav li a {
  color: red;
}
```

#### 3. 子选择器

也称子元素选择器，只能选择亲儿子，即最近一组的元素

```css
//中间用>
.nav>a {
  color: red;
}
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/fceaae55032cd76535e24c18765160e3.png)

#### 4. 并集选择器

可以选择多组标签。通常用于集体声明。逗号就是**和**的意思

> 需要用逗号分开。最后一个元素不要逗号

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/b149e3377ecc1b231e10471189a077c8.png)

```css
div, p, .pig li {
  color: red;
}
```

#### 5. 伪类选择器

伪类选择器用于向某些选择器添加特殊的效果，比如给链接添加特殊效果，或选择第1个，第n个元素。 

伪类选择器书写最大的特点是用冒号（:）表示，比如 :hover 、 :first-child 。

因为伪类选择器很多，比如有链接伪类、结构伪类等，所以这里先给大家讲解常用的链接伪类选择器。

#### 6. 链接伪类选择器

```css
/*未访问过*/
a:link{
  color: black;
  text-decoration: none;
}
/*鼠标点击过时*/
a:visited{
  color: orange;
}
/*鼠标悬浮时*/
a:hover{
  color: red;
}
/*鼠标按下未松开*/
a:active{
  color: green;
}
```

**注意事项：**

1. 为了确保生效，请按照**LVHA**的循顺序声明 :link－:visited－:hover－:active。
2. 记忆法：love hate 或者 lv 包包 hao。
3. 因为 a 链接在浏览器中具有默认样式，所以我们实际工作中都需要给链接单独指定样式。

**实际开发中的常用写法：**

```css
/* a 是标签选择器 所有的链接 */
a {
    color: gray;
}
/* :hover 是链接伪类选择器 鼠标经过 */
a:hover {
    color: red; /* 鼠标经过的时候，由原来的 灰色 变成了红色 */
}
```

#### 7. focus伪类选择器

用于选取获得焦点的表单元素。一般来说只有input类表单元素才能获取，因此是针对表单元素的。

```css
input:focus {
  background-color: pink;
}
```

#### 8. 复合选择器总结

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/84f93f8f4993ab6975857c99a58d6de8.png)

### 三、CSS元素显示模式

#### 1. 概念

可以将网页标签分类。HTML元素一般分为块元素和行内元素两种类型。

#### 2. 块元素

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/21252206235b001a162cb37b14656d07.png)

#### 3. 行内元素

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/7ca583ffccc9e8463a8b33c6113c48c4.png)

特别注意行内元素不能🙅‍放块元素！

链接里面不能放链接！但<a>里面可以放块级元素，但<a>转化成块级模式最安全。

#### 4. 行块内元素

同时具有两种元素的特点。

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/96939ba9014bf98aa57b639af0e575b9.png)

#### 5. 元素显示模式总结

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/5fc1519b254e280257e3785d96743cba.png)

#### 6. 元素显示模式转换

将一种模式转化成另一种模式。

如将<a>转化成块级元素：**（最常用）**

```css
a {
  width: 200px;
  height: 250px;
  display: block;
}
```

将<div>转化成行内元素：

```css
div {
  display: inline;
}
```

将<span>转化成行内块元素：

```css
span {
  width: 200px;
  height: 250px;
  display: inline-block;
}
```

**软件推荐：**

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/3102af384a1f7ec6670ae26c3315c725.png)

下载链接：https://zh.snipaste.com/download.html

#### 7. 文字垂直居中

让文字高度等于盒子高度

```css
div {
  height: 200px;
  line-height: 200px;
}
```

### 四、CSS的背景

#### 1. 背景颜色

默认是透明色

```css
div {
  background-color: transparent;
}
```

#### 2. 背景图片

常用于logo或者装饰性的小图片或者是超大背景图片，优势是便于控制位置（精灵图也是一种运用场景）。none是没有图片。

如：

```css
div {
  width: 200px;
  height: 250px;
  background-image: url("http://www.baidu.com.png");
}
```

#### 3. 背景平铺

```css
/*不平铺*/
background-repeat: no-repeat;
/*默认情况：*/
background-repeat: repeat;
/*沿着x轴平铺*/
background-repeat: repeat-x;
/*沿着y轴平铺*/
background-repeat: repeat-y;
```

#### 4. 背景图片位置

改变图片在背景中的位置。

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/b61ceb78461d6cd198304ee37b176bd9.png)

1.如果是**方位名词**，则没有先后关系。如果只写了一个，则另一个默认是center。

```css
background-position: center top;
```

> 注意：较大背景时会常用到上面的代码

2.如果是**精确单位**，那么第一个是x坐标，第二个是y坐标。

```css
background-position: 20px 50px;
```

> 注意，原点坐标是左上角。如果省略一个参数，则没省略的一定是x坐标，另一个默认是垂直居中。

3.如果是**混合单位**。第一个是x坐标，第二个是y坐标。

```css
background-position: 20px center;
```

#### 5. 背景图像固定（背景附着）

可以做视觉滚动效果。

```css
/*固定图像*/
background-attachment: fixed;
/*默认滚动*/
background-attachment: scroll;
```

#### 6. 背景复合写法

```css
body {
  background: black url("image/bg.jpg") no-repeat fixed center;
}
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/99f6077c095182bdfe3fdbebfab3fcba.png)

#### 7. 背景色半透明

```
background: rgba(0, 0, 0, 0.3);
```

第四个参数设置透明度，0是纯透明。习惯性把0给省略，即.3

这是CSS3新增属性。

#### 8. 背景总结

![img](https://img.zjgsuzjx.top/img/images/2021/06/09/c7ba556c23d46e3643a09cf7c0f862e2.png)

### 五、CSS三大特性

层叠性、继承性、优先级

#### 1. 层叠性

相同的选择器给设置系统的样式。即相同选择器的相同属性会出现冲突的情况。

重叠性原则：

最重要是**就近原则**。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/0ea4b0d92268c239ef7859e95c08ab7b.png" alt="0ea4b0d92268c239ef7859e95c08ab7b.png" border="0" />

#### 2. 继承性

子标签会继承父标签的某些样式，

```css
div {
  color: pink;
  font-size: 12px;
}
<div>
  <p>demo</p>
</div>
```

```
<p>标签会继承父亲<div>的属性。但不是所有样式都可以继承。
```

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/a1cff517ba7a0b041ff934d1142241c8.png" alt="a1cff517ba7a0b041ff934d1142241c8.png" border="0" />

而行高的继承可以不跟单位。如

```css
div {
  font: 12px/1.5 "Microsoft YaHei";
}
```

指的是当前文字大小的1.5倍。注意是当前的，而不是层叠之前的。

#### 3. 优先级

当同一个元素指定多个选择器时，就会有优先级产生。

原则：选择器相同，则执行重叠性；选择器不同，按照选择器优先级。

优先级如下：（依次变大）

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/e6b5dfa8058ec56b1c42e27eb483da6b.png" alt="e6b5dfa8058ec56b1c42e27eb483da6b.png" border="0" />

```css
div {
  color: pink!important;
}
.test {
  color: red;
}
```

**注意点：**

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/b696cc25287c6e78d50f9bba0129a97b.png" alt="b696cc25287c6e78d50f9bba0129a97b.png" border="0" />

```css
#father {
  color: red!important;
}
p {
  color: pink;
}
<div id="father">
  <p>demo</p>
</div>
```

注意这里继承过来的权重为0，最后还是粉色。

同时，上面这块代码还可以解释以下情况：

```css
body {
  color: red;
}
<a href="#">demo</a>
```

最后结果不是红色，因为浏览器默认制定了一个样式，即蓝色有下划线 a{color:blue}，继承的权重为0。

> 复合选择器还会有权重叠加的问题

如：

```css
ul li {
  color: green;
}
li {
  color: red;
}
```



> ul li的权重成了0 0 0 1 +0 0 0 1=0 0 0 2
>
> 同时叠加后不会有进位，如0 0 0 10

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/9c7881e543807317515ff303a857433f.png" alt="9c7881e543807317515ff303a857433f.png" border="0" />

## 三、CSS盒子模型

### 一、盒子模型

#### 1. 网页布局过程

1. 先准备好相关的网页元素，网页元素基本都是盒子 Box 。 
2. 利用 CSS 设置好盒子样式，然后摆放到相应位置。
3. 往盒子里面装内容。

> 核心：利用CSS设置好盒子位置。

#### 2. 盒子组成部分

CSS盒子模型本质上是一个盒子，封装周围的HTML元素，包括边框、外边框、内边距等等。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/6553c13d62571f1d2051b6ce85b40086.png" alt="6553c13d62571f1d2051b6ce85b40086.png" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/ddfb2173c7a3fa1bde5e4beee0ad2c09.png" alt="ddfb2173c7a3fa1bde5e4beee0ad2c09.png" border="0" />

#### 3. 边框（border）

border可以设置元素的边框。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/011a243b2904c594f30aa4e152bffeba.png" alt="011a243b2904c594f30aa4e152bffeba.png" border="0" />

```css
border-width: 5px;
border-style: solid;
border-color: pink;
```

边框简写：

```css
/*没有顺序*/
border: 1px solid red;
```

边框分开写法：

```css
border-top: 1px solid red;
border-bottom: 10px dashed purple;
```

利用层叠性设置上边框为黄色，其它边框为红色：

```css
border: 1px solid red;
border-top: 1px solid yellow;
```

#### 4. 表格的细线边框

```css
/*两个相邻边框合并一起*/
border-collapse: collapse;
```

> 一般测量时不量边框

#### 5. 内边距（padding）

```css
/*左内边距*/
padding-left: 20px;
/*上内边距*/
padding-top: 30px;
```

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/f2f5895d72811c5842a360d4d212c507.png" alt="f2f5895d72811c5842a360d4d212c507.png" border="0" />

内边距复合写法（简写）：

```css
/*一个值时，代表上下左右都是5px*/
padding: 5px;
/*两个值时，代表上下内边距是5，左右是10px*/
padding: 5px 10px;
/*三个值时，代表上是5，左右是10，下是20*/
padding: 5px 10px 20px;
/*四个值时，上是5，右是10，下是20，左是30*，采取顺序针方式*/
padding: 5px 10px 20px 30px;
```

内边距也影响盒子大小，因此要高度/宽度-2*内边距。

在设置导航栏中，因为字数不同会有不同的浪费空间，因此可以不设置width，通过设置padding来统一间隙。

在小米导航栏中，一般不同text-indent，而用padding。同时要修改宽度。

> 如果盒子本身没有制定width/height属性，则此时padding不会撑开盒子大小。可以通过继承来实验。

#### 6. 外边距

```css
/*下外边距为20*/
margin-bottom: 20px;
/*上外边距为20*/
margin-top: 20px;
margin-left: 20px;
margin-right: 20px;
```

上面代码和下面代码等价：

```
margin: 20px;
```

> 另外的复合写法于内边距写法相似。

外边距可以让块级盒子水平居中，有两个条件：

1.必须制定宽度

2.盒子左右的外边距都设置为auto

```css
margin: 0 auto;
/*或*/
margin-left: auto;
margin-right: auto;
/*或*/
margin: auto;
```

行内元素或者是行内块元素水平居中给其父元素添加text-align:center即可。

```css
.head {
  text-align: center;
}
```

#### 7. 外边距合并

父子元素设定外边距，可能会出现塌陷问题。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/93d81cdc99e97f7d84dd4aada4a97610.png" alt="93d81cdc99e97f7d84dd4aada4a97610.png" border="0" />

下面这种解决方案最佳，不会增大盒子。

```
overflow: hidden;
```

#### 8. 清除内外边距

网页元素很多都带有默认的内外边距，各个浏览器默认的也不一样。

万能解决方法：

```
* {
  padding: 0;
  margin: 0;
}
```

行内元素为了照顾其兼容性，尽量只设置左右内外边距，不要设置上下内外边距。（就算设置了也不会起效果）。但是转化为块级和行内块元素就可以设置。

### 二、PS基本操作

网页美工大部分效果图是用ps做的。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/35182acc573de2ee7658e4780b14c4af.png" alt="35182acc573de2ee7658e4780b14c4af.png" border="0" />

主要要记住测量和取色。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/fedac2ab110c85273db0764444569a57.png" alt="fedac2ab110c85273db0764444569a57.png" border="0" />

**--为什么布局用不同盒子？**

不同标签有不同的含义，合理的地方用合理的标签。

**--为什么用这么多的类名？**

给每一个盒子起一个名字，修改样式会非常灵活。后期维护也很方便。

**--到底用margin还是padding？**

其实可以混用，各有优缺点。但要根据实际情况，总有更简单的方法。

**--去掉li的项目符号：**

```
list-style: none;
```

### 三、圆角边框

盒子角落带圆角。

```
div {
  border-radius: 10px;
}
```

参数可以是数值也可以是**百分比**，如50%，指的是宽度和高度的一半。

原理：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/68a9c97f5607c478cff6e610b5d73533.png" alt="68a9c97f5607c478cff6e610b5d73533.png" border="0" />

制作一个圆形的盒子：

```css
div {
  width: 10px;
  height: 10px;
  border-radius: 5px;
}
```

制作圆角矩形：

```css
div {
  width: 10px;
  height: 6px;
  border-radius: 3px;
}
```

```css
/*分别对应左上角，右上角，右下角，左下角*/
border-radius: 1px 2px 3px 4px;
/*分别对应左上角、右下角和右上角、左下角*/
border-radius: 1px 2px;
```

也可以单独设置：

```css
border-top-left-radius: 20px;
```

### 四、盒子阴影

参数描述：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/cb36caf16758546ed8e2916d250b6342.png" alt="cb36caf16758546ed8e2916d250b6342.png" border="0" />

```css
div {
  box-shadow: 10px 10px 10px 10px rgba(0,0,0,.3);
}
```

> 要注意盒子阴影不占空间。

### 五、文字阴影

参数描述：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/1d60ef511edc7a39d82d626fc3afffd2.png" alt="1d60ef511edc7a39d82d626fc3afffd2.png" border="0" />

```css
div {
  text-shadow: 5px 5px 6px rgba(0,0,0,.3);
}
```

## 四、CSS浮动

### 一、浮动

#### 1. 传统网页布局三种方式

就是盒子怎么摆放顺序。

1.普通流（标准流）

2.浮动

3.定位

#### 2. 标准流（普通流/文档流）

也就是行内元素和块内元素按照规定好的方式来排列元素。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/6a5f72790514b9aff9bf19c677b64bf0.png" alt="6a5f72790514b9aff9bf19c677b64bf0.png" border="0" />

#### 3. 为什么要浮动

有很多布局效果，标准流无法实现，此时可以利用浮动完成布局。

> 因为浮动可以改变元素标签默认的排列方式。

典型应用：让多个块级元素一行内排列显示。

网页布局第一准则：多个块级元素纵向排列找标准流，多个块级元素横向排列找浮动。

语法及参数：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/55e57ab69a943515283f6e13c83220f4.png" alt="55e57ab69a943515283f6e13c83220f4.png" border="0" />

简单解释：加了浮动后会让盒子默认在同一行

```
div {
  float: left;
}
```

#### 4. 浮动特性

1.浮动元素会脱离标准流（脱标），并且**不再保留原来的位置**。浮动盒子在标准流盒子上面。

2.浮动的元素会一行内显示并且元素顶部对齐。**父级宽度装不下时，多出来的会另起一行显示。**

3.浮动的元素会具有行内块元素的特性。

> 任何元素都可以浮动。添加浮动之后会具有和行内块元素相似的性质，可以直接宽度和高度了。块级盒子没有设置宽度，默认宽度和父级一样宽，添加浮动以后，它的大小根据内容来决定。

#### 5. 父级标准流和子级浮动搭配使用

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/6c7bb7c4f7caeb5de1c1a7127aafee0b.png" alt="6c7bb7c4f7caeb5de1c1a7127aafee0b.png" border="0" />

> 准则：先设置盒子大小，在设置盒子位置。

### 二、常见网页布局

#### 1. 常见的网页布局（三种）

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/7981bb52cdacbc2ec6536465dd2dee6a.png" alt="7981bb52cdacbc2ec6536465dd2dee6a.png" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/54d14e2021d72dd90a9af92db738d3c4.png" alt="54d14e2021d72dd90a9af92db738d3c4.png" border="0" />

> 第三种最常见

#### 2. 浮动布局的注意点

1.浮动和标准流的父盒子搭配。**先用标准流的父元素排列上下位置，之后内部子元素采取浮动排列左右位置。**

2.一个元素浮动了，理论上其余的兄弟元素也要浮动。**浮动的盒子只会影响浮动盒子后面的标准流，不会影响前面的标准流。**

> 思考题：所有的父盒子都必须有高度吗？

答：不一定。比如一篇文章里字数越多，高度越多。不能写死高度。

### 三、清除浮动

#### 1. 为什么要清除浮动

因为父盒子在很多情况下，不方便给高度，但是子盒子浮动不占位置，最后父级盒子高度为0，就会影响下面的标准流盒子。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/14a37f6e331aa5af6aab190b6b5578d7.png" alt="14a37f6e331aa5af6aab190b6b5578d7.png" border="0" />

#### 2. 清除浮动的本质

就是清除浮动元素造成的影响。

#### 3. 清除浮动方法

语法：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/c579966c5357345402d9cbaee4a8b309.png" alt="c579966c5357345402d9cbaee4a8b309.png" border="0" />

策略是闭门浮动。

**1.额外标签法。**也称隔墙法。就是在最后一个浮动的标签后面加一个额外的标签。

```css
.clear {
  clear: both;
}
<div class="clear"></div>
```

**注意点：**

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/252f1db3c59bbf22f57e0de63336cbca.png" alt="252f1db3c59bbf22f57e0de63336cbca.png" border="0" />

**2.父级添加overflow属性**

给父级添加overflow属性，属性值为hiddern、auto、scroll

优点：代码简洁

缺点：无法显示溢出的部分

**3.父级添加after伪属性**

是额外标签法的升级版。

```css
.clearfix:after{
  content: "";
  display: block;
  height: 0;
  clear: both;
  visibility: hidden;
}

.clearfix{
  /*兼容IE6、7*/
  *zoom: 1;
}

<div class="box clearfix"></div>
```

缺点是照顾低版本浏览器。优点是没有增加标签。

**4.双伪元素清除浮动**

```css
.clearfix:before,.clearfix:after{
  content: "";
  display: table;
}
.clearfix:after {
  clear: both;
}
.clearfix{
  /*IE6\7*/
  *zoom: 1;
}
```

优点是代码更简洁。缺点是照顾低版本浏览器。代表网站有腾讯、小米等。

#### 4. 清除浮动总结

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/a4720ee1793ac531a922bdf8c5d3b0a4.png" alt="a4720ee1793ac531a922bdf8c5d3b0a4.png" border="0" />

### 四、PS切图

**常见的图片格式：**

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/f41075903358685621a5fc72bce45d05.png" alt="f41075903358685621a5fc72bce45d05.png" border="0" />

#### 1. 图层切图

最简单的切图方式：右击图层->快导出为png。

很多情况下要合并图层导出。选中需要的图层：图层菜单->合并图层（ctrl+e）

#### 2. 切片切图

切图->文件菜单->导出->存储为web->选择我们要的图片格式->存储

#### 3. PS插件切图

自动将你要的图层进行输出。

www.cutterman.cn

### 五、学成在线案例

#### 1. 学成在线准备工作

我们本次采取结构与样式相分离思想： 

1. 创建 study 目录文件夹 (用于存放我们这个页面的相关内容)。 
2. study 目录内新建 images 文件夹，用于保存图片。 
3. 新建首页文件 index.html（以后我们的网站首页统一规定为 index.html )。
4. 新建 style.css 样式文件。我们本次采用外链样式表。
5. 将样式引入到我们的 HTML 页面文件中。
6. 样式表写入清除内外边距的样式，来检测样式表是否引入成功。

#### 2. CSS属性书写顺序

建议遵循以下顺序： 

1. 布局定位属性：display / position / float / clear / visibility / overflow（建议 display 第一个写，毕竟关系到模式）
2. 自身属性：width / height / margin / padding / border / background
3. 文本属性：color / font / text-decoration / text-align / vertical-align / white- space / break-word
4. 其他属性（CSS3）：content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient 

#### 3. 页面布局整体思路

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/1f72aaaf2bf9a7fd0dbc3043cb3f47c4.png" alt="1f72aaaf2bf9a7fd0dbc3043cb3f47c4.png" border="0" />

导航栏注意点：实际开发中，我们不会直接用链接a而是用li包含链接（li+a）的做法。因为li+a语义更清晰；直接用啊，搜索引擎容易辨别为由堆砌关键期的嫌疑，从而影响网站排名。

#### 4. 头部制作

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/b73ad84463103d065642a39bacf9014f.png" alt="b73ad84463103d065642a39bacf9014f.png" border="0" />

#### 5. banner制作

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/50daa8077a087ccabfb381dae9d8a946.png" alt="50daa8077a087ccabfb381dae9d8a946.png" border="0" />

> ✨浮动的盒子不会由外边距浮动的问题

#### 6. 精品模块

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/a3f6cc45f78bf9f59a790bd02471e87b.png" alt="a3f6cc45f78bf9f59a790bd02471e87b.png" border="0" />

> ✨行高是可以继承的

#### 7. 精品推荐大模块

- 1 号盒子为最大的盒子， box 版心水平居中对齐

- 2 号盒子为上面部分，box-hd -- 里面左侧标题 H3 左浮动，右侧链接 a 右浮动

- 3 号盒子为底下部分，box-bd -- 里面是无序列表，有 10 个小 li 组成

- 小 li 外边距的问题，这里有个小技巧：给 box-hd 宽度为 1215 就可以一行装开 5 个 li

#### 8. 底部模块

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/9d39ec6cc1e16c800c6d225b30bb3080.png" alt="9d39ec6cc1e16c800c6d225b30bb3080.png" border="0" />

## 五、CSS定位

### 一、定位

#### 1. 为什么需要定位

1.某个元素可以自由的在一个盒子内移动位置，并且压住其他盒子。

2.某些盒子可以固定在屏幕某个位置

#### 2. 定位组成

将盒子定在某一个位置。定位=定位模式+边偏移。

1.定位模式

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/ff1310d881a41b795c3da70346724c2c.png" alt="ff1310d881a41b795c3da70346724c2c.png" border="0" />

2.边偏移

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/8138f11e2121122bdc295d450c948429.png" alt="8138f11e2121122bdc295d450c948429.png" border="0" />

#### 3. 静态定位

是元素默认的定位方式，无定位的意思。

静态定位==标准流，没有边偏移。

#### 4. 相对定位 relative

是相对于它原来的位置而言移动的。原来在标准流的位置继续占有，后面的盒子仍然以标准流的方式对待它。（即不会动。不会脱标）

#### 5. 绝对定位 absolute

移动位置时是相对于它祖先元素来说的。如果没有父元素，则以浏览器为准；如果有父级，但父元素没有定位，还是以浏览器为准；如果有祖先级且祖先元素有定位（相对、绝对、固定定位），则以**最近一级**带有定位的元素为准。绝对定位不再占用原来的位置（脱标）。

#### 6. 子绝父相的由来

> 子级是绝对定位的话，父级要用相对定位。

因为父级要保留位置，子级不需要保留位置。

#### 7. 固定定位 fixed

可以固定于浏览器**可视区**的某个位置。

以浏览器的可视窗口为参照点移动元素。跟父元素没有任何关系。不随滚动条滚动。固定位置不占有原来的位置。也是一种特殊的绝定位。

> 固定定位小技巧：固定在版心右侧位置。

小算法：

1.让固定定位的盒子left:50%，走到浏览器可视区的一半位置。

2.让固定定位的盒子margin-left:版心宽度的一般距离。

#### 8. 粘性定位

可以认为是相对得和固定定位的混合。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/284df92a39f561b0d6cfaef78c1897be.png" alt="284df92a39f561b0d6cfaef78c1897be.png" border="0" />

#### 9. 定位的总结

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/de4348f10e1d4d2393dd0792d332209f.png" alt="de4348f10e1d4d2393dd0792d332209f.png" border="0" />

#### 10. 定位叠放次序

利用z-index来控制盒子的前后次序（z轴）。

语法：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/bf1309d9b136c2bf2d7b5e613b69d095.png" alt="bf1309d9b136c2bf2d7b5e613b69d095.png" border="0" />

数值越大，盒子越靠上。**数字后面不加单位。只有定位的盒子才有z-index属性。**

#### 11. 定位的扩展

1.如果用了绝对定位，则用margin:auto不会起效果，且会让前面设置的margin覆盖无效化。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/683da12f7e58e5195af62f9089e7b4b0.png" alt="683da12f7e58e5195af62f9089e7b4b0.png" border="0" />

2.定位的特殊性：

**行内元素**添加绝对或者是固定定位，可以直接设置高度和宽度；**块级元素**添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小。

3.**脱标的盒子不会触发外边距塌陷。**

> 4.绝对定位（固定定位）会完全压住盒子。而浮动元素只会压住下面标准流的盒子，但是不会压住下面标准流盒子里的文字或图片。

> ✨注意：如果一个盒子既有left属性也有right属性，则默认会执行left属性。

```css
.last {
  left: 0;
}
.last {
  right: 0;
}
```

### 二、网页布局总结

通过盒子模型，清楚知道大部分html标签是一个盒子。通过CSS浮动、定位 可以让每个盒子排列成为网页。一个完整的网页，是标准流、浮动、定位一起完成布局的，每个都有自己的专门用法。

1. **标准流** 可以让盒子上下排列或者左右排列，垂直的块级盒子显示就用标准流布局。 
2. **浮动** 可以让多个块级元素一行显示或者左右对齐盒子，多个块级盒子水平显示就用浮动布局。 
3. **定位** 定位最大的特点是有层叠的概念，就是可以让多个盒子前后叠压来显示。如果元素自由在某个盒子内移动就 用定位布局。

### 三、元素的显示与隐藏

本质：让一个元素在页面中隐藏或者显示出来。

#### 1. display属性

```css
div {
  /*隐藏属性*/
  display: none;
}
```

隐藏元素后，不再占用位置。可以搭配JS。用的更多一些。

#### 2. visibility可见性

```css
div {
  /*隐藏属性*/
  visibility: hidden;
  /*显示属性*/
  visibility: visible;
}
```

隐藏元素后，继续占有原来的位置。

#### 3. overflow溢出

```css
div {
  /*隐藏超出部分*/
  overflow: hidden;
  /*一直显示滚动条*/
  overflow: scroll;
  /*超出才显示滚动条*/
  overflow: auto;
  /*默认*/
  overflow: visible;
}
```

一般情况下，不希望溢出部分显示出来。但是如果有定位的盒子，慎用overflow:hidden，因为它会隐藏多余的部分。

**经过某图层再显示遮罩层：**

```css
.tudou:hover .mask{
  display: block;
}
```

## 六、CSS高级技巧

### 一、精灵图

#### 1. 为什么要精灵图

网页图像过多，服务器会频繁接受和发送请求图片，造成服务器压力过大，这将大大降低页面的加载速度。为了有效减少服务器请求次数，提高页面的加载速度，出现了CSS精灵技术（CSS Sprites、CSS 雪碧）。

#### 2. 精灵图的使用

主要是针对背景图片使用。就是把多个小背景图片整合到一个图片里。移动背景图片位置，此时可以使用background-position。**移动的距离就是目标图片的x和y**，一般情况是往上往左移动，所以数值是**负值**。使用精灵图的时候需要精确测量每个小背景图片的大小和位置。

```css
.p{
  width: 200px;
  height: 200px;
  background: url("images/xx.jpg") no-repeat -200px -50px;
}
```

### 二、字体图标

主要用于显示网页中通用、常用的一些小图标。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/f60a51d0e5bba454002bde9d6e666b9a.png" alt="f60a51d0e5bba454002bde9d6e666b9a.png" border="0" />

字体图标iconfont。展示的是图标，本质属于字体。

#### 1. 优点

轻量级、灵活性、兼容性。

- 轻量级：一个图标字体要比一系列的图像要小。一旦字体加载了，图标就会马上渲染出来，减少了服务器请求

- 灵活性：本质其实是文字，可以很随意的改变颜色、产生阴影、透明效果、旋转等

- 兼容性：几乎支持所有的浏览器，请放心使用

但是不能替代精灵图标，只是对工作中图标部分技术的提升和优化。

如果遇到一些结构和样式比较简单的小图标，就用字体图标；如果比较复杂的就用精灵图标。

#### 2. 字体图标下载

icomoon字库：http://icomoon.io

阿里inconfont字库：http://www.iconfont.cn

#### 3. 字体图标的引用（针对第一个网站）

1.把下载包里面的fonts文件夹放入页面根目录下

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/dff7073231e46f0b767c6ed6ce8a317c.png" alt="dff7073231e46f0b767c6ed6ce8a317c.png" border="0" />

2.通过css引入

在CSS样式中全局声明字体。如：

```css
@font-face {
  font-family: 'icomoon';
  src:  url('fonts/icomoon.eot?eyysvl');
  src:  url('fonts/icomoon.eot?eyysvl#iefix') format('embedded-opentype'),
  url('fonts/icomoon.ttf?eyysvl') format('truetype'),
  url('fonts/icomoon.woff?eyysvl') format('woff'),
  url('fonts/icomoon.svg?eyysvl#icomoon') format('svg');
  font-weight: normal;
  font-style: normal;
  font-display: block;
}
```

3.html标签内添加小图标。

复制到需要的地方。

4.设置字体

```css
span{
  font-family: 'icomoon';
}
```

#### 4. 字体图标的追加

当需要添加新的字体图标时：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/2f955974eb21742df2d1bc50a928b2c0.png" alt="2f955974eb21742df2d1bc50a928b2c0.png" border="0" />

### 三、CSS三角

做出三角形。

```css
.box {
  position: absolute;
  right: 15px;
  top: -10px;
  /*宽和高必须是0*/
  width: 0;
  height: 0;
  line-height: 0;
  font-size: 0;
  border: 50px solid transparent;
  border-left-color: pink;
  margin: 100px auto;
}
```

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/10116b1daf434cd9c121ff8854e71851.png" alt="10116b1daf434cd9c121ff8854e71851.png" border="0" />

### 四、CSS用户界面样式

#### 1. 鼠标样式 cursor

```css
<p style="cursor: default">默认样式</p>
<p style="cursor: pointer">小手样式</p>
<p style="cursor: move">移动样式</p>
<p style="cursor: text">文字样式</p>
<p style="cursor: not-allowed">禁止样式</p>
```

#### 2. 轮廓线 outline

取消轮廓线：

```css
input {
  outline: none;
}
```

#### 3. 防止拖拽文本域

```css
textarea{
  resize: none;
}
```

### 五、vertical-align的使用

使用场景：机场用于设置图片或者表单（行内块元素）和文本垂直对齐。只针对行内元素或行内快元素有效。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/6d9da7a21813f7d98f6385a87b48c38b.png" alt="6d9da7a21813f7d98f6385a87b48c38b.png" border="0" />

默认是baseline。

```css
img {
  vertical-align: bottom;
  vertical-align: top;
  vertical-align: middle;
}
```

#### 1. 消除图片底部默认空白缝隙问题

图片底部会有一个空白缝隙，原因是行内块元素会和文字的基线对齐。

解决方案：**推荐**

```
img {
  vertical-align: bottom;
  vertical-align: middle;
}
```

或者

```
img {
  display: block;
}
```

### 六、溢出的文字省略号显示

#### 1. 单行文本溢出

```css
div {
  /*默认，自动换行*/
  white-space: normal;
  /*强制一行内显示*/
  white-space: nowrap;
  /*溢出部分隐藏*/
  overflow: hidden;
  /*溢出部分省略号显示*/
  text-overflow: ellipsis;
}
```

#### 2. 多行文本溢出显示省略号

```css
div {
  height: 100px;
  width: 50px;
  overflow: hidden;
  text-overflow: ellipsis;
  /*弹性伸缩盒子模型显示*/
  display: -webkit-box;
  /*限制在一块元素显示文本的行数*/
  -webkit-line-clamp: 5;
  /*设置或检索伸缩盒对象的子元素的排列方式*/
  -webkit-box-orient: vertical;
}
```

### 七、常见布局技巧

#### 1. margin负值的应用

让每个盒子margin往左移动-1px正好压住相邻盒子边框。

```css
div {
  float: left;
  height: 100px;
  width: 50px;
  border: 1px solid red;
  /*因为边框是1px*/
  margin-left: -1px;
}
```

鼠标经过某个盒子的时候，提高当前盒子的层级即可。（如果没有定位，要加相对定位；如果有定位，则加z-index）

```css
/*第一种*/
ul li:hover {
  position: relative;
  border: 1px solid black;
}
/*第二钟*/
ul li:hover {
  z-index: 1;
  border: 1px solid black;
}
```

#### 2. 文字围绕浮动元素

可以巧妙运用浮动元素不会压住文字的特性。

#### 3. 行内块技巧运用

页码在页面中间显示: 

1. 把这些链接盒子转换为行内块， 之后给父级指定 text-align:center; 
2. 利用行内块元素中间有缝隙，并且给父级添加 text-align:center; 行内块元素会水平会居中

#### 4. CSS三角强化

```css
.a {
  width: 0;
  height: 0;
  border-top: 100px solid transparent;
  border-right: 50px solid skyblue;
  border-bottom: 0 solid blue;
  border-left: 0 solid green;
}
```

以此可以制作一个三角形。

或者简写：

```css
.a {
  width: 0;
  height: 0;
  border-color: transparent red transparent transparent;
  border-style: solid;
  border-width: 100px 50px 0 0;
}
```

### 八、CSS初始化

不同浏览器对于某些百年的默认值是不同的，为了消除不同浏览器对HTML文本呈现的差异，照顾浏览器的兼容，我们需要对CSS初始化。（CSS reset）

Unicode编码字体：把中文字体的名称用相应的Unicode编码来代替，这样就可以有效的避免浏览器解释CSS代码时候出现乱码的问题。如黑体 \9ED1\4F53

## 七、HTML5和CSS3提高

### 一、HTML5新特性

增加了一些新的标签、表单和表单属性。

IE9+以上版本的浏览器才支持。

如：<header>、<nav>、<article>、<section>、<aside>、<footer>

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/59a18a03de0d8f08cd6fceea12adbb20.png" alt="59a18a03de0d8f08cd6fceea12adbb20.png" border="0" />

> 主要是针对搜索引擎的。移动端也偏向于这些标签。

#### 1. 新增的多媒体标签

音频：<audio>、视频：<video>。可以不依赖flash和插件。

**1.视频<video>：**尽量使用mp4格式，兼容性较强。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/6b22e340c2070745a892511ecbe55f85.png" alt="6b22e340c2070745a892511ecbe55f85.png" border="0" />

语法：

```
<video src="文件地址" controls="controls"></video>
```

常见的属性：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/e223ad44fe24c4cd0c34d0861a521ef3.png" alt="e223ad44fe24c4cd0c34d0861a521ef3.png" border="0" />

**2.音频<audio>：**

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/f6c1aa9bd5a1a6f738b07aa0a65624f0.png" alt="f6c1aa9bd5a1a6f738b07aa0a65624f0.png" border="0" />

常见属性：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/7f53b3a542afb32210226227803ee086.png" alt="7f53b3a542afb32210226227803ee086.png" border="0" />

```
<audio src="文件地址" autoplay="autoplay" controls="controls"></audio>
```

**3.多媒体标签总结：**

- 音频标签和视频标签使用方式基本一致
- 浏览器支持情况不同
- 谷歌浏览器把音频和视频自动播放禁止了
- 我们可以给视频标签添加 muted 属性来静音播放视频，音频不可以（可以通过JavaScript解决）
- 视频标签是重点，我们经常设置自动播放，不使用 controls 控件，循环和设置大小属性

#### 2. 新增的input类型

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/808f72566a0ee74bf9c1968d3daa6782.png" alt="808f72566a0ee74bf9c1968d3daa6782.png" border="0" />

下面可以测试：

```html
<form action="">
  <ul>
    <li><input type="submit" value="提交"></li>
  </ul>
</form>
```

#### 3. 新增的表单属性

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/cf1b1346a81ea4eff38a9bb2c7cd66c4.png" alt="cf1b1346a81ea4eff38a9bb2c7cd66c4.png" border="0" />

如：

```css
<form action="">
  <input type="text" name="" id="" required="required" placeholder="pink老师" >
  <input type="submit" value="提交">
</form>
```

```css
<form action="">
  <input type="file" multiple="multiple">
</form>
```

> ✨tips：快速生成->input:text；修改样式->input::placeholder {color: pink;}

### 二、CSS3新特性

#### 1. CSS3的现状

新增的CSS3样式有兼容性问题，ie9+才支持。移动端支持优于PC端。

新增选择器：属性选择器、结构伪类选择器和伪元素选择器。

#### 2. 属性选择器

```css
/*必须是input，但是同时具有value这个属性才会被更改*/
input[value] {
  color: pink;
}
<input type="file" value="demo">
```

```css
/*还可以根据属性值来选择*/
input[type=text] {
  color: pink;
}
```

```css
/*选择div有class属性且开头是icon*/
div[class^=icon] { }
```

```css
/*选择div有class属性且结尾是icon*/
div[class$=icon] { }
```

```css
/*选择div有class属性且含有icon*/
div[class*=icon] { }
```

> 类选择器、属性选择器、伪类选择器，权重都是10。

#### 3. 结构伪类选择器

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/f6317047bd8459a5cfcf37e23559f554.png" alt="f6317047bd8459a5cfcf37e23559f554.png" border="0" />

如：

```css
/*选择第一个叫li的孩子*/
ul li:first-child { }
/*选择第n个叫li的孩子*/
ul li:nth-child(4) { }
/*选择所有偶数的孩子*/
ul li:nth-child(even) { }
```

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/04a2ee5ae20f909232c2cd20b3e38716.png" alt="04a2ee5ae20f909232c2cd20b3e38716.png" border="0" />

```css
/*选择第一个叫li的孩子*/
ul li:first-of-type { }
/*选择第n个叫li的孩子*/
ul li:nth-of-type(4) { }
/*选择所有偶数的孩子*/
```

> ✨注意：nth-of-type执行时，先看类型，再看第几个；而nth-child先看第几个，再看类型。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/c05cd212e8852ac0336a00bb3be2b983.png" alt="c05cd212e8852ac0336a00bb3be2b983.png" border="0" />

**小结：**

- 结构伪类选择器一般用于选择父级里面的第几个孩子
- nth-child 对父元素里面所有孩子排序选择（序号是固定的） 先找到第n个孩子，然后看看是否和E匹配
- nth-of-type 对父元素里面指定子元素进行排序选择。 先去匹配E ，然后再根据E 找第n个孩子
- 关于 nth-child（n） 我们要知道 n 是从 0 开始计算的，要记住常用的公式
- 如果是无序列表，我们肯定用 nth-child 更多
- 类选择器、属性选择器、伪类选择器，权重为 10

#### 4. 伪元素选择器

可以利用CSS创建新标签元素，而不需要HTML标签，从而简化HTML结构。

::before（在元素内部前面插入内容） ::after（在元素内部后面插入内容）

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/5e400f635dad64d5a04e5563d7d10813.png" alt="5e400f635dad64d5a04e5563d7d10813.png" border="0" />

```css
div::before {
  /*必须有引号*/
  content: 'demo';
}
```

> 这是行内元素，且必须有content属性，权重是1。

**应用1：**做一个v

```css
div::after {
  /*反斜杠转译*/
  position: absolute;
  top: 10px;
  right: 10px;
  content: '\e91e';
}
```

**应用2**：土豆

```css
.tudou:hover::before {
  display: block;
}
```

**应用3：**伪元素清除浮动

```css
.clearfix:before,.clearfix:after {
  content: '';
  /*转换成块级元素且在一行显示*/
  display: table;
}
.clearfix:after {
  /*清除浮动核心代码*/
  clear:both;
}
```

#### 5. CSS3盒子模型

为了不撑开盒子大小，可以固定住盒子大小。

```css
div {
  /*盒子大小默认为width+padding+border*/
  box-sizing: content-box;
  /*盒子大小为width，前提是padding+border不会超过width*/
  box-sizing: border-box;
}
```

同时可以拓展为：

```css
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
```

#### 6. CSS 2D转换

转换(transform)可以理解为变形。

##### 二维坐标系

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/8665277e832c8e47b8a799ed91f0c631.png" alt="8665277e832c8e47b8a799ed91f0c631.png" border="0" />

##### 移动translate

```css
div {
    width: 100px;
    height: 250px;
    /*分别是x,y轴上移动位置*/
    transform: translate(10px, 0px);
}
```

或者

```
transform:translateX(100px);
```

若

```
transform:translateX(100px);
transform:translateY(100px);
```

则只会改变Y，X还是为0。

> 最大的优点是不会影响其它元素的位置。百分比单位是相对与自身元素的。对行内标签没有效果。

```
/*分别是x的宽度、高度的50%*/
transform:translate(50%, 50%);
```

##### 旋转rotate

让元素在二维平面内顺时针旋转或者逆时针旋转。需要加单位deg。度角为正时，顺时针；负时，逆时针。默认旋转的中心点时元素的中心点。

```
transform: rotate(45deg);
```

给头像做旋转效果：

```css
img {
    width: 100px;
    /*过渡写到本身上，给谁过渡给谁加*/
    transition: all 0.3s;
}
img:hover {
    transform: rotate(360deg);
}
```

##### 转换中心点transform-origin

我们可以设置元素转换的中心点。transform-origin:x y;默认是元素的中心点(50% 50%)。也可以是：

```css
/*左下角*/
transform-origin: left bottom;
/*x、y像素*/
transform-origin: 50px 50px;
```

##### 缩放scale

可以控制元素放大还是缩小。

> 优势之处是：不会影响其它盒子，而且还可以修改中心点。

```css
/*里面写的数字不跟单位，就是倍数的意思，1就是本身大小*/
transform: scale(1, 2);
/*修改成一样的倍数*/
transform: scale(2);
/*缩小*/
transform: scale(0.5);
```

做出图片放大特效：

```css
div{
    float: left;
    overflow: hidden;
    margin: 100px 200px;
}
img {
    transition: all 0.5s;
}
div img:hover {
    transform: scale(1.2);
}

<div>
    <a href="#"><img src="xxx.jpg" alt=""></a>
</div>
```

##### 2D转换综合写法

中间用空格隔开，如：

```css
transform: translate(50px, 50px) rotate(180deg);
```

> 有顺序问题。先写位移，再写旋转和缩放。

##### 总结

- 转换transform 我们简单理解就是变形 有2D 和 3D 之分
- 我们暂且学了三个 分别是 位移 旋转 和 缩放
- 2D 移动 translate(x, y)   最大的优势是不影响其他盒子， 里面参数用%，是相对于自身宽度和高度来计算的
- 可以分开写比如 translateX(x)  和 translateY(y)
- 2D 旋转 rotate(度数)    可以实现旋转元素   度数的单位是deg
- 2D 缩放 sacle(x,y)   里面参数是数字 不跟单位 可以是小数   最大的优势 不影响其他盒子
- 设置转换中心点 transform-origin : x y;    参数可以百分比、像素或者是方位名词
- 当我们进行综合写法，同时有位移和其他属性的时候，记得要将位移放到最前面

#### 7. CSS动画

可通过设置多个节点控制一个或一组动画。分为两步：先定义动画；在使用动画。

##### 动画的基本使用

1.用keyframes定义动画（类似定义类选择器）

一打开页面自动运行

```css
/*move是名字，自己定义的*/
@keyframes move {
    /*开始状态*/
    0% {
        transform: translateX(0px);
    }
    100% {
        transform: translateX(1000px);
    }
}
div {
    width: 250px;
    height: 250px;
    background-color: pink;
    /*调用动画*/
    animation-name: move;
    /*持续时间*/
    animation-duration: 2s;
}
```

**所谓动画序列：**

- 0% 是动画的开始，100% 是动画的完成。这样的规则就是动画序列。
- 在 @keyframes 中规定某项 CSS 样式，就能创建由当前样式逐渐改为新样式的动画效果。
- 动画是使元素从一种样式逐渐变化为另一种样式的效果。您可以改变任意多的样式任意多的次数。
- 请用百分比来规定变化发生的时间，或用关键词 "from" 和 "to"，等同于 0% 和 100%。

**上面动画等价于：**

```css
@keyframes move {
    /*开始状态*/
    from {
        transform: translateX(0px);
    }
    to {
        transform: translateX(1000px);
    }
}
```

做出四角游动特效：

```css
@keyframes move {
    0% {
        transform: translate(0,0);
    }
    /*百分比要求整数，含义是总的时间的划分，如有10s的话，0%到25%就是2.5s*/
    25% {
        transform: translate(1000px,0);
    }
    50% {
        transform: translate(1000px,500px);
    }
    75% {
        transform: translate(0,500px);
    }
    100% {
        transform: translate(0,0);
    }
}
```

##### 动画常用属性

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/65798e41df3dc3d3ceb2edf3fa624d82.png" alt="65798e41df3dc3d3ceb2edf3fa624d82.png" border="0" />

##### 动画简写属性

animation:动画名称 持续时间 运动曲线 何时开始 播放次数 是否反方向 动画起始或者结束的状态;

如：（前两个不能省略）

```css
animation: move 2s linear 0s 1 alternate forwards;
```

**补充：**

```css
/*steps意思是分几步来完成动画*/
animation: move 2s steps(5) alternate forwards;
```

奔跑的小熊案例：

```css
body {
    background-color: #ccc;
}

div {
    position: absolute;
    width: 200px;
    height: 100px;
    background: url(media/bear.png) no-repeat;
    /* 我们元素可以添加多个动画， 用逗号分隔 */
    animation: bear .4s steps(8) infinite, move 3s forwards;
}

@keyframes bear {
    0% {
        background-position: 0 0;
    }
    100% {
        background-position: -1600px 0;
    }
}

@keyframes move {
    0% {
        left: 0;
    }
    100% {
        left: 50%;
        /* margin-left: -100px; */
        transform: translateX(-50%);
    }
}
```

#### 8. 3D转换

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/3fadecd7c3d3e7f87afc049d2540275a.png" alt="3fadecd7c3d3e7f87afc049d2540275a.png" border="0" />

记住z轴往外面是正值，往里面是负值。垂直屏幕。

##### 3D位移

transform：translateZ()一般用px单位。是沿着Z轴移动。记住xyz不能省略，如果没有就写0.

```css
transform: translateZ(100px);
transform: translateX(100px) translateY(200px) translateZ(100px);
/*简写写法*/
transform: translate3d(100px, 200px, 100px);
```

##### 透视（perspective）

如果需要在网页产生3D立体效果，就需要透视。透视也称为视距，就是人的眼睛到屏幕的距离。距离视觉点越近在电脑平面成像越大。单位是像素。

透视写在被观察元素的父盒子上面。

概念图：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/9056eb741b55c6499738f0ac4eb9694f.png" alt="9056eb741b55c6499738f0ac4eb9694f.png" border="0" />

##### 3D旋转 rotate3d

```css
body {
    perspective: 300px;
}
div {
    transition: all 0.5s;
}
div:hover {
    transform: rotateX(180deg);
}
```

> 左手定则：大拇指指向x轴、y轴、z轴正方向，四指为旋转方向。

```css
/*表示y轴旋转，xz不旋转，旋转45度*/
transform: rotate3d(0,1,0,45deg);
/*相当于向量做加法，结果是沿着对角线旋转*/
transform: rotate3d(1,1,0,45deg);
```

##### 3D呈现 transform-style

控制子元素是否开启三位立体环境。写给父级，影响的是子盒子。

```css
/*默认不开启3d立体空间*/
transform-style: flat;
/*子元素开启立体空间*/
transform-style: preserve-3d;
```

**翻转表白盒子案例：**

```css
<style>
    body {
        perspective: 500px;
    }
    .box {
        position: relative;
        transform-style: preserve-3d;
        width: 200px;
        height: 200px;
        margin: 200px auto;
        transition: all 1s;
    }
    .front, .back {
        position: absolute;
        top: 0;
        left: 0;
        width: 200px;
        height: 200px;
        line-height: 200px;
        color: white;
        border-radius: 50%;
        font-size: 20px;
        text-align: center;
    }
    .front {
        background-color: pink;
    }
    .back {
        background-color: skyblue;
        transform: rotateY(180deg);
    }
    .box:hover {
        transform: rotateY(-180deg);
    }
</style>
```

```html
<body>
    <div class="box">
        <div class="front">我是ZJX</div>
        <div class="back">我在CUMT等你</div>
    </div>
</body>
```



> 注意：如果写多个样式，要先写移动再写其它样式。✨但是也有例外，看需求，如果旋转的话，xyz轴也会跟着一起旋转的。

```css
transform: translateY(100px) rotateY(-90deg);
```

#### 9. 浏览器私有前缀

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/6c0b6ed0ec42d23094b4eb6ceefc0047.png" alt="6c0b6ed0ec42d23094b4eb6ceefc0047.png" border="0" />

#### 10. CSS其它特性

CSS3滤镜filter：将元素变模糊或颜色便宜

```css
.img {
  /*数值越大越模糊*/
  filter: blur(5px);
}
```

CSS3 calc函数：在声明CSS属性时可以执行一些计算。

```css
div {
  width: calc(100% - 30px);
}
```

#### 11. CSS过渡

可以从一个状态慢慢过渡到另一个状态。使页面更好看。给谁过渡给谁加。

1. 属性：想要变化的 css 属性， 宽度高度 背景颜色 内外边距都可以 。如果想要所有的属性都 变化过渡， 写一个all 就可以。

2. 花费时间：单位是 秒（必须写单位） 比如 0.5s 
3. 运动曲线：默认是 ease （可以省略）
4. 何时开始 ：单位是 秒（必须写单位）可以设置延迟触发时间 默认是 0s （可以省略）

```css
transition: 要过渡的属性 花费时间 运动曲线 何时开始;
div {
  width: 100px;
  height: 250px;
  background-color: pink;
  transition: width .5s ease-in .1s;
}
div:hover {
  width: 200px;
}
```

如果要改多个属性：中间加逗号

```css
transition: width .5s ease-in .1s, height .5s ease 1s;
```

如果要让属性都发生变化：

```css
transition: all .5s;
```

### 三、狭义的HTML5 CSS3

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/0e50b7fe3cc0c5500308191f7a0f37aa.png" alt="0e50b7fe3cc0c5500308191f7a0f37aa.png" border="0" />

#### 1. 广义的HTML5

是HTML5本身+CSS3+JavaScript

## 八、品优购项目实战

### 一、项目规划

#### 1. 网站制作流程

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/13df3496b7a83091e9f59aa92c91bafa.png" alt="13df3496b7a83091e9f59aa92c91bafa.png" border="0" />

#### 2. 开发工具以及技术栈

1. **开发工具** 

   VScode 、Photoshop（fw）、主流浏览器（以Chrome浏览器为主）

2. **技术栈**

   - 利用 HTML5 + CSS3 手动布局，可以大量使用 H5 新增标签和样式

   - 采取结构与样式相分离，模块化开发

   - 良好的代码规范有利于团队更好的开发协作，提高代码质量，因此品优购项目里面，请同学们遵循以下代码规范。

#### 3. 模块化开发

很多样式和结构在很多页面都会出现，比如页面的头部和尾部，大部分页面都有。可以**把这些结构和样式单独作为一个模块**，然后重复使用。

#### 4. 网站favicon图标

先切成png图片，再通过第三方网站转化成ico图标，如http://www.bitbug.net。在<head>里引入。

#### 5. 网站TDK三大标签SEO优化

SEO汉译为搜索引擎优化，是一种利用搜索引擎的规则提高网站在有关搜索引擎内自然排名的方式。从而提高网站的知名度。

> TDK=title+description+keyword

**titile：**建议网站名 - 网站的介绍（尽量不超过30个字）

**description：**简要说明我们网站主要是做声明的。

**keyword：**是页面关键词，是搜索引擎的关注点之一。

### 二、首页制作

#### 1. 常用模块类名命名

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/a97d8bd75980da7a2f64ac9b9139afd3.png" alt="a97d8bd75980da7a2f64ac9b9139afd3.png" border="0" />

#### 2. LOGO SEO优化

1. logo 里面首先放一个**h1**标签，目的是为了提权，告诉搜索引擎，这个地方很重要。

2. h1 里面再放一个**链接**，可以返回首页的，把 logo 的背景图片给链接即可。

3. 为了搜索引擎收录我们，我们链接里面要放**文字（网站名称）**，但是文字不要显示出来。

   - 方法1：**text-indent** 移到盒子外面**（text-indent: -9999px)** ，然后 **overflow:hidden** ，淘宝的做法。

   - 方法2：直接给 **font-size: 0;** 就看不到文字了，京东的做法。 

4. 最后给链接一个 **title** 属性，这样鼠标放到 logo 上就可以看到提示文字了。

#### 3. Tab栏原理（和JS搭配）

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/626af3c9888633d8c73fd686ee84101b.png" alt="626af3c9888633d8c73fd686ee84101b.png" border="0" />

> 一般情况下，a如果包含有宽度的盒子，a需要转为块级元素。

### 三、列表页制作

1. 列表页面是新的页面，我们需要新建页面文件 **list.html** 。
2. 因为列表页的**头部**和**底部**基本一致，所以我们需要把首页中的头部和底部的结构复制过来。
3. 头部和底部的样式也需要，因此 list.html 中还需要引入 **common.css** 。
4. 需要新的 **list.css** 样式文件，这是列表页专门的样式文件。

### 四、注册页制作

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/ac67bee0b2e387ccf6c4f387ba429f87.png" alt="ac67bee0b2e387ccf6c4f387ba429f87.png" border="0" />

### 五、Web服务器

#### 1. 什么是Web服务器

也称为主机，也是一台计算机。一般是指网站服务器。服务器在网络位置不同，可以分为本地服务器和远程服务器。

#### 2. 本地服务器

就是把自己的电脑作为服务器，同一个局域网内的电脑可以访问自己的电脑网站。利用ajax。

#### 3. 远程服务器

通常是别的公司为我们提供一台电脑。可以上传后通过域名访问。

#### 4. 将自己网站上传远程服务器

一般服务器是收费的，如阿里云。

推荐免费的远程服务器（免费空间）http://free.3v.do

1. 去免费空间网站注册账号。
2. 记录下主机名、用户名、密码、域名。
3. 利用 cutftp 软件 上传网站到远程服务器。
4. 在浏览器中输入域名，即可访问我们的品优购网站了。

### 六、课程总结

1. HTML我们学的就是常用标签， 就是基本盒子 

2. CSS 就是用来美化布局网页。 

3. HTML+CSS是没有逻辑可言的，基本就是搭积木摆放盒子的过程，你需要的是耐心。 

4. 对同学们来说，现在最困难的是 布局结构 。欠缺分析页面布局的能力, 

5. 同一个模块，有很多布局方式，能做出来就是好的。 
6. 多看别人写的页面，模仿人家的布局，每次写页面总会有新的收获。 
7. 错误总是在所难免，一定要学会利用chrome 调试工具， 他们能快速帮我们排查错误。你还需要细心。 8.学好定位，对后面学习JavaScript 有很大的帮助。

## 九、移动WEB开发之流式布局

### 一、移动端基础

#### 1. 浏览器现状

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/640437ead911031df8fb020c4ec4f63e.png" alt="640437ead911031df8fb020c4ec4f63e.png" border="0" />

移动端兼容性很好。

#### 2. 收集屏幕现状

- 移动端设备屏幕尺寸非常多，碎片化严重。

- Android设备有多种分辨率：480x800, 480x854, 540x960, 720x1280，1080x1920等，还有传说中的2K，4k屏。

- 近年来iPhone的碎片化也加剧了，其设备的主要分辨率有：640x960, 640x1136, 750x1334, 1242x2208等。

- 作为开发者无需关注这些分辨率，因为我们常用的尺寸单位是 px 。

#### 3. 常见尺寸

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/ab2a5df65186933bd6f5fe94f86e14da.png" alt="ab2a5df65186933bd6f5fe94f86e14da.png" border="0" />

#### 4. 移动端调式方法

- Chrome DevTools（谷歌浏览器）的模拟手机调试

- 搭建本地web服务器，手机和服务器一个局域网内，通过手机访问服务器

- 使用外网服务器，直接IP或域名访问

总结：移动端浏览器我们主要对webkit内核进行兼容；移动端针对手机端开发。

### 二、视口

视口就是浏览器显示页面内容的屏幕区域。可以分为布局视口、视觉视口和理想视口。

#### 1. 布局视口 layout viewport

解决早期PC端页面在手机上显示的问题。只不过元素看上去很小，需要手动缩放页面。

#### 2. 视觉视口 visual viewport

就是用户当前看到的区域。

#### 3. 理想视口 ideal viewport

使网站在移动端有理想的浏览。需要手动添加meta视口标签贴纸浏览器操作。目的是使布局视口的宽度和理想视口的宽度一致。

#### 4. meta视口标签

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/9071624eba94efabf6bff86dfe28e326.png" alt="9071624eba94efabf6bff86dfe28e326.png" border="0" />

标准的viewport设置：

```html
<meta name="viewport"
      content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```

### 三、二倍图

#### 1. 物理像素&物流像素比

物流像素点指的是屏幕显示的最小颗粒，是物理正是存在的。开发的时候1px不一定对于1个物理像素。在PC端1px等于1个物理像素点，但是移动端不同。一个px能显示的物理像素点个数被称为物理像素比或屏幕像素比。

#### 2. 多倍图

对于一张50px*50px的图片，在收集Retina屏中打开，会按照物流像素比放大倍数，造成图片模糊。因此要刻意准备一张多倍图然后在css中进行缩放，在移动端放大后就不会再模糊。

#### 3. 背景缩放 background-size

```css
background: url("image1.jpg") no-repeat;
/*对背景图片进行缩放*/
background-size: 500px 200px;
/*百分比是相对于父盒子来说的*/
background-size: 50%;
/*使背景图片一直等比例拉伸直到完全盖住盒子*/
background-size: cover;
/*缩放/拉到短边*/
background-size: contain;
```

> ✨多倍图切图可以使用cutterman插件

### 四、移动端开发选择

#### 1. 移动端主流方案

单独制作**移动端**页面（主流）、**响应式**页面兼容移动端（其次）

#### 2. 单独制作移动端页面

通过判断设备来打开相应的页面。

#### 3. 响应式页面兼容移动端

通过判断屏幕宽度来改变样式，以适应不同终端。缺点是制作麻烦，需要花很大距离去调兼容性问题。

### 五、移动端技术解决方案

#### 1. CSS初始化 normalize.css

移动端初始化推荐。http://necolas.github.io/normalize.css

#### 2. 特殊样式

```css
/*CSS3盒子模型*/
box-sizing: border-box;
-webkit-box-sizing: border-box;
/*清除点击高亮*/
-webkit-tap-highlight-color: transparent;
/*清除外观效果*/
-webkit-appearance: none;

/*禁止长按页面时的弹出菜单*/
img, a {
    -webkit-touch-callout: none;
}
```

### 六、移动端常见布局

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/d7f881c2a03b1264117a49ad3836127c.png" alt="d7f881c2a03b1264117a49ad3836127c.png" border="0" />

#### 1. 流式布局（百分比布局）

也称非固定像素布局。通过盒子的宽度设置成百分比来根据屏幕的宽度来进行缩放，不受固定像素的限制，内容向两侧填充。在web移动端开发比较常见。**可以通过max-width和min-width来限制盒子拉伸幅度**。

如：

```css
body {
    width: 100%;
    min-width: 320px;
    max-width: 640px;
    margin: 0 auto;
    font-size: 14px;
    font-family: -apple-system, Helvetica, sans-serif;
    color: #666;
    line-height: 1.5;
}
```

**精灵图的缩放问题：**

需要先将精灵图等比例缩放；然后再测量坐标；在background-size也要缩放，注意这里缩放的值是缩放后精灵图的宽和高。

## 十、移动WEB开发之flex布局

### 一、flex布局体验

传统布局：兼容性好；布局繁琐；局限性。flex弹性布局：操作简单，布局非常简单，移动端应用广泛；PC端支持情况差；IE11以下不支持。

### 二、flex布局原理

flex是flexible Box的缩写，意为弹性布局，用来为盒装模型提供最大的灵活性，任何一个容器都可以指定为flex布局。当我们为父盒子设为flex布局以后，子元素的float、clear和vertical-align属性将失效。伸缩布局=弹性布局=伸缩盒布局=弹性盒布局=flex布局。

采用Flex布局的元素，成为Flex容器，简称容器。它的所有子元素自动成为容器成员，成为Flex项目，简称项目。子容器可以横向排列也可以纵向排列。

因此Flex的布局原理就是通过给父盒子添加Flex属性，来控制子盒子的位置和排列方式。

### 三、flex布局父项常见属性

#### 1. 常见的父项属性

以下由6个属性是对父元素设置的

- flex-direction：设置主轴的方向

- justify-content：设置主轴上的子元素排列方式

- flex-wrap：设置子元素是否换行

- align-content：设置侧轴上的子元素的排列方式（多行）

- align-items：设置侧轴上的子元素排列方式（单行）

- flex-flow：复合属性，相当于同时设置了 flex-direction 和 flex-wrap

#### 2. flex-direction 设置主轴方向

**主轴和侧轴：**默认主轴方向就是x轴方向，水平向右；默认侧轴方向就是y轴方向，水平向下。

```css
div {
    display: flex;
    width: 800px;
    height: 350px;
    /*默认的主轴是x轴，我们的元素是跟着主轴排列的*/
    flex-direction: row;
    /*翻转排列*/
    flex-direction: row-reverse;
    /*将主轴设置为y轴*/
    flex-direction: column;
}
```

#### 3. justify-content 设置主轴上的子元素排列方式

> 要确定好主轴是哪一个。

```css
div {
    display: flex;
    width: 800px;
    height: 350px;
    flex-direction: row;
    /*默认从头部对齐*/
    justify-content: flex-start;
    /*右边对齐*/
    justify-content: flex-end;
    /*居中对齐*/
    justify-content: center;
    /*平均分配剩余空间*/
    justify-content: space-around;
    /*先两边贴边，再分配剩余空间*/
    justify-content: space-between;
}
```

#### 4. flex-wrap设置子元素是否换行

默认情况下，项目都排列在一行上，装不下的话会缩小子元素的宽度。

```css
div {
    display: flex;
    width: 800px;
    height: 350px;
    /*默认不换行*/
    flex-wrap: nowrap;
    /*换行*/
    flex-wrap: wrap;
}
```

#### 5. align-items设置侧轴上的子元素排列方式（单行）

```css
div {
    display: flex;
    width: 800px;
    height: 350px;
    /*默认主轴是x轴*/
    justify-content: center;
    /*我们需要一个侧轴居中*/
    align-items: center;
    /*沿着侧轴方向拉伸，前提是没有高度*/
    align-items: stretch;
}
```

> ✨千万要分辨好主轴和侧轴的方向。

#### 6. align-content设置侧轴上的子元素排列方式（多行）

设置子项在侧轴上的排列方式并且**只能用于子项出现换行的情况（多行）**，**在单行下是没有效果的。**

```css
div {
    display: flex;
    width: 800px;
    height: 350px;
    /*换行*/
    flex-wrap: wrap;
    /*默认在侧轴的头部开始排列*/
    align-content: flex-start;
    /*在侧轴中间显示*/
    align-content: center;
    /*子项在侧轴先分布在两头，再评分剩余空间*/
    align-content: space-between;
    /*子项再侧轴平分剩余空间*/
    align-content: space-around;
}
```

#### 7. align-content和align-items的区别

1.align-items适合于当行情况下，只有上对齐、下对齐、居中和拉伸

2.align-content适合于换行（多行）的情况下，可以设置上对齐、居中、拉伸以及平均分配剩余空间等属性值。

3.总结就是单行找align-items，多行找align-content

#### 8. flex-flow

```css
div {
    display: flex;
    width: 800px;
    height: 350px;
    flex-direction: column;
    flex-wrap: wrap;
    /*上面代码等价于*/
    flex-flow: row wrap;
}
```

### 四、flex布局子项常见属性

#### 1. flex属性

就是从剩余空间去分配份数。

**比如设置移动端导航栏：中间占一份**

```css
section div:nth-child(1) {
    /*设置宽高*/
}
section div:nth-child(2) {
    flex: 1;
}
section div:nth-child(3) {
    /*设置宽高*/
}
```

又比如：

```css
section div:nth-child(1) {
    /*占四分之一*/
    flex: 1;
}
section div:nth-child(2) {
    /*站二分之一*/
    flex: 2;
}
section div:nth-child(3) {
    /*占四分之一*/
    flex: 1;
}
```

#### 2. align-self控制子项自己在侧轴上的排列方式

允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

```css
span:nth-child(2) {
    align-self: flex-end;
}
```

#### 3. order属性定义项目的排列顺序

可以定义项目的先后排列顺序，并且不需要改动标签。和z-index不一样。

```css
span:nth-child(2) {
    /*默认是0，将排到前面*/
    order: -1;
}
```

### 五、携程网案例

使用flex来制作。

```css
body {
    max-width: 540px;
    min-width: 320px;
    margin: 0 auto;
    font: normal 14px/1.5 Tahoma, "Lucida Grande", Verdana, "Microsoft Yahei", STXihei, hei;
    color: #000;
    background: #f2f2f2;
    /*隐藏水平滚动条*/
    overflow-x: hidden;
    /*取消点击高亮*/
    -webkit-tap-highlight-color: transparent;
}
```

> ✨注意固定定位的盒子跟父级没有关系，它是以屏幕为准，因此需要指定max-width；有了绝对定位后，margin会失效；flex里不会出现外边距合并问题。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/29b4d24dc6bcfa5d927deacd9b4c6b96.png" alt="29b4d24dc6bcfa5d927deacd9b4c6b96.png" border="0" />

**快速修改图标：**

```css
.local-nav li [class^="local-nav-icon"] {
    width: 32px;
    height: 32px;
    margin-top: 8px;
    background: url(../images/localnav_bg.png) no-repeat 0 0;
    background-size: 32px auto;
}

.local-nav li .local-nav-icon-icon2 {
    background-position: 0 -32px;
}
```

**背景颜色渐变：（线性）**

```css
/*背景渐变必须添加浏览器私有前缀*/
background: -webkit-linear-gradient(left, red, blue);
/*默认从下往下*/
background: -webkit-linear-gradient(red, blue);
/*或者从左上往右下*/
background: -webkit-linear-gradient(top left, red, blue);
```

**flex还可以写%：**

```css
/*是相对于父级来说的*/
flex: 20%;
```

## 十一、移动WEB开发之rem适配布局

### 一、rem基础

rem(root em)是一个单位，类似于em，em是相对于父元素的字体大小来说的。不同的是rem的基准是相对于html元素的字体大小。因此可以通过修改html字体大小来改变里面元素的大小。

如：

```css
html {
    font-size: 14px;
}
div {
    height: 20rem;
    width: 20rem;
    background-color: pink;
}
```

### 二、媒体查询

媒体查询（Media Query）是CSS3新语法。

使用@media查询，可以针对不同的媒体类型定义不同的样式。**@media可以针对不同的屏幕尺寸设置不同的样式**。当重置浏览器大小时，页面也会根据浏览器的宽度和高度重新渲染页面。

```css
/*这句话的意思时在屏幕上，且最大宽度是800像素*/
/*媒体查询可以根据不同的屏幕尺寸来改变不同的样式*/
@media screen and (max-width: 800px){
    body {
        background-color: pink;
    }
}
@media screen and (max-width: 500px){
    body {
        background-color: green;
    }
}
```

> @media 参数1 参数2 （参数3）{样式表}

参数1是媒体类型：all（所有设备）、print（用于打印机）、screen（用于电脑和手机屏幕）

参数2是关键字：and、not、only

参数3是媒体特征，必须有小括号：如width、min-width、max-width

如根据不同的宽度来改变页面背景颜色：

```css
/*媒体查询一般按照从小到大或者从大到小的顺序来写*/
@media screen and (max-width: 539px){
    body {
        background-color: pink;
    }
}
@media screen and (min-width: 540px) and (max-width: 969px){
    body {
        background-color: green;
    }
}
@media screen and (min-width: 970px) {
    body {
        background-color: blue;
    }
}
```

> and和px不能省略。

#### 1. 引入资源

针对不同的媒体使用不同的样式表。

```html
<!--    引入资源就是针对不同的屏幕尺寸调用不同的css文件-->
    <link rel="stylesheet" href="1-2.css" media="screen and (min-width:320px)">
    <link rel="stylesheet" href="1-3.css" media="screen and (min-width:640px)">
```

### 三、less基础

CSS弊端：没有变量，无法计算；代码没有逻辑性，冗余度过高；不方便维护，不利于复用。

#### 1. Less介绍

Less（Leaner Style Sheets），是一门CSS扩展语言，也称为CSS预处理器。为CSS加入程序式语言的特性。引入了变量、Mixin、运算以及函数等功能，大大简化了CSS的编写，降低了CSS的维护成本。

官方中文：http://lesscss.cn/

**常见的CSS预处理器**：Sass、Less、Stylus

> 总结：Less是一门CSS预处理语言，扩展了CSS的动态特性。

#### 2. Less使用

需要新建一个后缀名为less的文件，在这个less文件里面书写less语句。

**1. Less变量**

> 变量是指没有固定的值，可以改变的。必须以@为前缀；不能包含特殊字符；不能以数字开头；大小写敏感。

```less
//定义一个粉色的变量
@color1: pink;
body {
  background-color: @color1;
}
div {
  background-color: @color1;
}
```

**2. Less编译**

Less包含一套自定义的与语法以及一个解析器，用户定义的样式的规则最终会通过解析器，编译生成对应的CSS文件。因此我们需要编译less文件。

在webstorm中需要先安装node.js，然后用npm安装插件。

**3. Less嵌套**

选择器的嵌套写法如：（在xxx.less文件）

```less
div {
  width: 200px;
  height: 200px;
  background-color: pink;
  a {
    color: red;
  }
}
```

> 如果遇到伪类、交集、伪元素选择器（应该加&）。内层选择器的前面没有&复合，则它被解析为父选择器的后代；如果有&符号，它就被解析为父元素自身或父元素的伪类。

如：（在xxx.less文件）

```less
div {
  width: 200px;
  height: 200px;
  background-color: pink;
  &::after {
    color: red;
  }
  &:hover {
    color: red;
  }
}
```

**4. Less运算**

任何颜色、数字或变量都可以参与运算。

如：（在xxx.less文件）

```less
//实现加法运算
@border: 5px + 5;
div {
  //减法
  width: 200px - 50;
  //乘法
  height: 200px * 2;
  border: @border solid red;
}
img {
  //除法
  width: 82 / 64rem;
}
```

> ✨注意运算符左右有空格；两个数参与运算，如果只有一个数有单位，则最后的结果以这个单位为准；如果两个数参与运算且都有单位，单位不一样，最后的结果以第一个单位为准。

> 🎀现在是2021年，less已经进入4.0时代，除法两边需要加括号了。

颜色也可以参与运算：（在xxx.less文件）

```less
background-color: #666666 - #222222;
```

### 四、rem适配方案

1. 让一些不能等比自适应的元素，达到当设备尺寸发生改变的时 候，等比例适配当前设备。
2. 使用媒体查询根据不同设备按比例设置html的字体大小，然后 页面元素使用rem做尺寸单位，当html字体大小变化元素尺寸 也会发生变化，从而达到等比缩放的适配。

#### 1. rem实际开发适配方案

按照设计稿与设备宽度的比例，动态计算并设置htnl根标签的font-size大小（媒体查询）；CSS中，设计稿元素的宽、高、相对位置等取值，按照同等比例换算为rem为单位的值。

#### 2. rem适配方案技术使用（市场主流）

第一种是less、媒体查询、rem；第二钟是flesible.js、rem。

1.**第一种**：一般情况以一套或两套效果图适应大部分的屏幕，牺牲一些效果。

**动态设置html标签font-size大小：**

① 假设设计稿是750px

② 假设我们把整个屏幕划分为15等份（划分标准不一可以是20份也可以是10等份）

③ 每一份作为html字体大小，这里就是50px

④ 那么在320px设备的时候，字体大小为320/15 就是 21.33px

⑤ 用我们页面元素的大小 除以不同的 html 字体大小会发现他们比例还是相同的

⑥ 比如我们以 750为标准设计稿

⑦ 一个100*100像素的页面元素 在 750屏幕下， 就是 100 / 50 转换为rem 是 2rem * 2 rem 比例是 1比1

⑧ 320屏幕下， html 字体大小为 21.33 则 2rem = 42.66px 此时宽和高都是 42.66 但是 宽和高的比例还是 1比1

⑨ 但是已经能实现不同屏幕下 页面元素盒子等比例缩放的效果

**元素大小取值方法：**

① 最后的公式： 页面元素的rem值 = 页面元素值（px） / （屏幕宽度 / 划分的份数）

② 屏幕宽度/划分的份数 就是 html font-size 的大小

③ 或者：页面元素的rem值 = 页面元素值（px） / html font-size 字体大小

> 个人笔记：划分的份数不会改变最后元素呈现的大小，之所以需要这个值，只是在需要改变html字体大小时，能够等比例改变元素的大小。可用数学公式推导。

2.**第二种**：简介高效的rem适配方案flexible.js

手机淘宝团队出的简洁高效移动端适配库我们再也不需要在写不同屏幕的媒体查询，因为里面js做了处理。它的原理是把当前设备划分为10等份，但是不同设备下，比例还是一致的。 我们要做的，就是确定好我们当前设备的html 文字大小就可以了。比如当前设计稿是 750px，那么我们只需要把 html 文字大小设置为 75px(750px / 10) 就可以。里面页面元素rem值： 页面元素的px 值 / 75。剩余的，让flexible.js来去算

下载地址：https://github.com/amfe/lib-flexible

### 五、苏宁首页案例

#### 1. 设置公共common.less文件

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/d95f3d572c40b5295ea19f255f455957.png" alt="d95f3d572c40b5295ea19f255f455957.png" border="0" />

#### 2. 在less文件中引入其它less文件

```less
@import "common";
```

#### 3. body样式

```less
body {
  min-width: 320px;
  //body的元素大小=宽度，因此根据公式body的rem=份数
  width: 15rem;
  margin: 0 auto;
  //父元素设置line-height:1.5会直接继承给子元素，子元素根据自己的font-size再去计算子元素自己的line-height。
  //父元素设置line-height:150%是计算好了line-height值，然后把这个计算值给子元素继承，子元素继承拿到的就是最终的值了。此时子元素设置font-size就对其line-height无影响了。
  line-height: 1.5;
  font-family: Arial, Helvetica;
}
```

#### 4. 其它

```less
.search-content {
  //可以直接写，因为最后是跟着html的font-size大小变的，这里全部按照设计稿的宽度运算。
  position: fixed;
  top: 0;
  width: 15rem;
  height: (78rem / 50);
}
```

```less
.search {
  flex: 1;
  input {
    //去掉蓝色边框
    outline: none;
    width: 100%;
    border: 0;
    height: 66rem / @baseFont;
    border-radius: 33rem / @baseFont;
    background-color:#FFF2CC;
    margin-top: 12rem / @baseFont;
    font-size: 25rem / @baseFont;
    padding-left: 55rem / @baseFont;
    color: #757575;
  }
}
```

> 记住行内元素不能左右居中对齐，需要转换成块级元素。

#### 5. 使用适配方案2来制作案例

```html
<!--引入js文件-->
<script src="flexible.js"></script>
```

#### 6. px自动转rem插件

webstorm插件PXTOREM，VSCODE插件cssrem

由于js里设定了根据当前屏幕大小来设定font-size，因此为了限定最大为750px，我们需要在css里添加以下代码：

```less
@media screen and (min-width: 750px){
  html {
    font-size: 75px!important;
  }
}
```

## 十二、移动WEB开发之响应式布局

### 一、响应式开发

#### 1. 响应式开发原理

就是使用媒体查询针对不同宽度的设备进行布局和样式的设置，从而适配不同设备的目的。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/3bb76c38f3784af7dddde4bd8c452aa4.png" alt="3bb76c38f3784af7dddde4bd8c452aa4.png" border="0" />

#### 2. 响应式布局容器

响应式需要一个父级做为布局容器，来配合子元素来实现变化效果。原理是通过媒体查询来改变不同屏幕下的布局容器的大小，在改变里面子元素的排列方式和大小。

**平时我们的响应式尺寸划分：**

- 超小屏幕（手机，小于 768px）：设置宽度为 100%
- 小屏幕（平板，大于等于 768px）：设置宽度为 750px
- 中等屏幕（桌面显示器，大于等于 992px）：宽度设置为 970px
- 大屏幕（大桌面显示器，大于等于 1200px）：宽度设置为 1170p

**响应式导航案例**

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/74a2b87ac526500ffbfb7d729269fbca.png" alt="74a2b87ac526500ffbfb7d729269fbca.png" border="0" />

```css
.container {
    width: 750px;
    margin: 0 auto;
}
.container ul li {
    float: left;
    width: 93.75px;
    height: 30px;
    background-color: green;
}
/*屏幕缩放到767px以下时，改变容器布局*/
@media screen and (max-width: 767px) {
    .container {
        width: 100%;
    }
    .container ul li {
        width: 33.33%;
    }
}
```

### 二、Bootstrap前端开发框架

#### 1. Bootstrap简介

是目前最受欢迎的前端框架。它是基于HTML、CSS和JavaScript的，结构灵活，使得Web开发更加快捷。

中文官网：http://www.bootcss.com/

官网：http://getbootstrap.com/

**推荐使用**：http://bootstrap.css88.com/

目前版本：https://v5.bootcss.com/

**框架含义**：顾名思义就是一套架构，**它有一套比较完整的网页功能解决方案**，而且控制权在框架本身，有预制样式库、组件和插件。使用者要按照框架所规定的某种规范进行开发。

**优点：**

1.标准化的html+css编码规范

2.提供了一套简介、直观、强悍的组件

3.有自己的生态圈，不断的更新迭代

4.让开发更简单，提高了开发的效率

#### 2. Bootstrap使用

目前只考虑它的样式表的使用。分四步曲。

**1.创建文件夹结构**

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/76fc8c0b24e160bfd52eacebfda47c22.png" alt="76fc8c0b24e160bfd52eacebfda47c22.png" border="0" />

**2.创建html骨架结构**

```html
<!--[if IE 8]>
    .... some HTML here ....
<![endif]-->
```

条件注释定义只有 Internet Explorer 执行的 HTML 标签。

```html
<!--推荐注释，如果浏览器小于IE9，则会引入这两个文件，否则不引入-->
<!--[if lt IE 9]>
<!--解决ie9以下浏览器对html新标签的不识别问题-->
<script src="https://cdn.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
<!--解决ie9以下浏览器对css3 Media Query的不识别问题 -->
<script src="https://cdn.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
<![endif]-->
```

```html
<!--要求当前网页使用IE浏览器最高版本的内核来渲染-->
<meta http-equiv="X-UA-Compatible" content="ie=edge">
```

**3.引入相关样式文件**

可以下载后引入，或者直接引入官方的：

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-olOxEXxDwd20BlATUibkEnjPN3sVq2YWmYOnsMYutq7X8YcUdD6y/1I+f+ZOq/47" crossorigin="anonymous">
```

**4.书写内容**

可以直接拿Bootstrap预先定义好的样式来使用；或者修改Bootstrap原来的样式，注意权重问题。

如：

```html
<button type="button" class="btn btn-secondary">Secondary</button>
<button type="button" class="btn btn-success logo">Success</button>
<button type="button" class="btn btn-danger">Danger</button>
```

之后可以在其基础上修改：（若修改失败，考虑权重问题）

```css
.logo {
    width: 200px;
    height: 300px;
}
```

#### 3. 布局容器

Bootstrap已经定义好了容器类，叫.container。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/15debf752442f3516636e576d2aa7006.png" alt="15debf752442f3516636e576d2aa7006.png" border="0" />

### 三、Bootstrap栅格系统

#### 1. 简介

英文grid system，它是指将网页布局划分为等宽的列，然后通过列数的定义来模块化页面布局。

Bootstrap提供了一套响应式、移动设备优先的流失栅格系统，随着屏幕或视口尺寸的增加，系统会自动分为最多12列。

![img](https://api.bilibili.com/x/note/image?image_id=56945)

> 和rem划分屏幕的区别在于，bootstrap只划分内容部分（container），而rem划分整个屏幕。

#### 2. 栅格系统参数

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/204497606d868d474e16a3b3ab0836c2.png" alt="204497606d868d474e16a3b3ab0836c2.png" border="0" />

行（row）必须放到container布局容器里面；实现列的平均划分时，需要给列添加类前缀。

```html
<div class="container">
    <!--刚好加起来为12份，占满容器的整行-->
    <div class="row">
        <div class="col-lg-6">1</div>
        <div class="col-lg-2">2</div>
        <div class="col-lg-2">3</div>
        <div class="col-lg-2">4</div>
    </div>
</div>
```

如列数加起来小于12，则占不满；大于12则会另起一行来显示。

> 可以同时为一列指定多个设备的类名，以便划分不同的份数

如：

```html
<div class="container">
    <div class="row">
        <div class="col-lg-1 col-md-3 col-sm-1">1</div>
        <div class="col-lg-2 col-md-3 col-sm-1">2</div>
        <div class="col-lg-2 col-md-3 col-sm-1">3</div>
        <div class="col-lg-7 col-md-3 col-sm-1">4</div>
    </div>
</div>
```

#### 3. 列嵌套

```html
<div class="container">
    <div class="row">
        <div class="col-lg-2">
            <!--列嵌套最好加一个row，这样可以取消父元素的padding值，而且高度会自动继承父元素-->
            <div class="row">
                <div class="col-md-2">1</div>
                <div class="col-md-2">2</div>
            </div>
        </div>
    </div>
</div>
```

#### 4. 列偏移

让两个盒子左右两侧对齐：

```html
<div class="container">
    <div class="row">
        <div class="col-md-4">1</div>
        <div class="col-md-4 offset-md-4">2</div>
    </div>
</div>
```

让一个盒子居中对齐：

```html
<div class="container">
    <div class="row">
        <div class="col-md-8 offset-md-2">1</div>
    </div>
</div>
```

#### 5. 列排序

```html
<div class="container">
    <div class="row">
        <!--order表示权重，越小越靠前，已废弃push和pull-->
        <div class="col-md-8 order-8">1</div>
        <div class="col-md-4 order-1">2</div>
    </div>
</div>
```

#### 6. 响应式工具

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/65c92e4db74248231c4a9dac542a59df.png" alt="65c92e4db74248231c4a9dac542a59df.png" border="0" />

> 可以利用以上的用法来展示和隐藏页面内容。

### 四、阿里百秀首页案例

#### 1. 屏幕划分分析

① 屏幕缩放发现 中屏幕 和 大屏幕布局 是一致的。 因此我们列 定义为 col-md- 就可以了， md 是大于等于 970 以上的

② 屏幕缩放发现 小屏幕 布局发生变化，因此我们需要为 小屏幕根据需求改变布局

③ 屏幕缩放发现 超小屏幕布局又发生变化，因此我们需要为 超小屏幕根据需求改变布局

④ 策略：我们先布局 md以上的 pc端布局，最后根据实际需求在修改 小屏幕 和 超小屏幕的 特殊布局

#### 2. 手动修改container的最大宽度

```css
@media screen and (min-width: 1280px){
    .container {
        width: 1280px;
    }
}
```

#### 3. 引入字体图标

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.5.0/font/bootstrap-icons.css">
```

**用i标签引入：**

```html
<i class="bi bi-emoji-smile-fill"></i>
```

**自己修改样式：**

```css
.bi-emoji-smile-fill {
    padding-right: 10px;
}
```

#### 4. 制作响应式

max-width:100%是，父级元素长度大于自身图片宽度时，用自身宽度；小于自身宽度时用父级宽度。

logo的响应式：（V3.0）

```css
/* 2. 我们事先准备好一个盒子 在logo里面，它平时是隐藏起来的，只有在超小屏幕下显示 */

.logo span {
    display: block;
    height: 50px;
    line-height: 50px;
    color: #fff;
    font-size: 18px;
    text-align: center;
}
```

```html
<img src="images/logo.png" alt="" class="hidden-xs">
<span class="visible-xs">阿里百秀</span>
```

**导航栏的响应式：**

```css
/* 当我们进入 小屏幕 还有 超小屏幕的时候 我们 nav 里面的li 浮动起来 并且宽度为 20%  */
@media screen and (max-width: 991px) {
    .nav li {
        float: left;
        width: 20%;
    }
    article {
        margin-top: 10px;
    }
}
```

```css
/* 当我们进入 超小屏幕的时候 我们 nav 文字会变成14px  */
@media screen and (max-width: 767px) {
    .nav li a {
        font-size: 14px;
        padding-left: 3px;
    }
}
```

### 五、移动端布局总结

#### 1. 移动端主流方案

<img src="https://img.zjgsuzjx.top/img/images/2021/06/17/5d8c6fa9177610c5404788ffc67828aa.png" alt="5d8c6fa9177610c5404788ffc67828aa.png" border="0" />

#### 2. 移动端技术选型

- 流式布局（百分比布局）

- lex 弹性布局（推荐）

- rem适配布局（推荐）

- 响应式布局

> 建议： 我们选取一种主要技术选型， 其他技术做为辅助，这种混合技术开

## 十三、移动WEB开发之vw和vh

flex布局的新趋向：rem **-->** vw和vh。

**vw和vh**

vw和vh是相对单位。vw是viewport width，vh是viewport height。1vw=1/100视口宽度，1vh=1/100视口高度。PC端不要用。

> 和百分比的区别：百分比是相对于父元素来说的，而vw和vh总是针对于当前视口来说的。

```css
div {
    width: 50vw;
    height: 50vh;
    background-color: #333;
}
```

按照375像素的设计稿来说，要放入一个50*50像素的盒子，则宽度=50/3.75vw.

>  开发中基本只是用vw，因为本质是根据视口的宽度来等比缩放页面元素高度和宽度的，所以不用管vh。

> 2021流行的切图软件：像素大厨

查兼容性的网站：https://caniuse.com/

下载别人网站字体图标：检查元素->iconfont样式表->负值字体URL到浏览器地址栏

## 十四、黑马面面项目

### 一、关于切图

可以用https://www.mockplus.cn/来切图使用，下载ps插件。

### 二、swiper插件

官网地址：https://www.swiper.com.cn/

用于制作轮播图。

1.下载需要的css和js文件  html页面中 引入相关文件

2.官网找到类似案例，复制html结构，css样式  js 语法

3.根据需求定制修改模块

### 三、上传码云并发布部署静态网站