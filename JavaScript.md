> 💥此MD/PDF/HTML文档由 [@竹梦者也]([竹梦者也 - ZJXのBLOG (zjgsuzjx.top)](https://www.zjgsuzjx.top/)) 编辑制作，不可转载❌、打印❌、二次编辑❌、贩卖❌。仅供学习交流使用，下载后切勿随意传播。
>
> 📌欢迎在留言区提供修改建议~
>
> 
>
> ✅2021.6.22	 @竹梦者也(https://www.zjgsuzjx.top) 



## 一、计算器编程基础

### 一、编程语言

#### 1. 编程

**编程：**就是让计算机为解决某个问题而使用某种程序设计语言编写程序代码，并最终得到结果的过程。

**计算机程序：**就是计算机所执行的一系列的指令集合，而次序全部都是用我们所掌握的语言来编写的。

> 注意：上面定义的计算机指的是任何能够执行代码的设备，如手机、ATM机等等。

#### 2. 计算机语言

**计算机语言指**用于人与计算机之间通讯的语言，它是人与计算机之间传递信息的媒介。

可以分为三大类，机器语言、汇编语言和高级语言。

计算机最终执行的是**机器语言**，二进制是计算机语言的基础。

#### 3. 编程语言

就是用来控制计算机的一系列指令，它有固定的格式和词汇。

如今的编程语言有两种形式：**汇编语言和高级语言**。

汇编语言和机器语言实质相同，都是直接对硬件操作；而高级语言包含了很多编程语言，如C、C++等等。

#### 4. 翻译器

将编程语言翻译成为机器语言，也称为二进制文件。

#### 5. 编程语言和标记语言的区别

编程语言有很强的逻辑和行为能力，是主动的；标记语言不用向计算机发出指令，常用于格式化和链接，他是被动的。

### 二、计算机基础

计算机有两部分组成，硬件和软件。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/18/e4565d1734da916b86203435915b0e1f.png" alt="e4565d1734da916b86203435915b0e1f.png" border="0" />

#### 1. 数据存储

计算机内部都使用二进制来表示数据。硬盘、内存都是保存的二进制数据。

#### 2. 数据存储单位

bit < byte < KB <GB < TB < ...

#### 3. 程序运行

1.当打开某个程序时，先从硬盘中把程序的代码加载到内存中。

2.CPU执行内存中的代码。

> 注意：之所以需要内存，是因为CPU运行太快了，如果只从硬盘中读数据，会浪费CPU性能，所以需要内存来保存运行时的数据。

## 二、初识JavaScript

### 一、初识JavaScript

#### 1. JavaScript历史

由布兰登·艾奇设计，最初叫LiveScript。与Java毫无关系。

#### 2. JavaScript是什么

是世界上最流行的语言之一，是一种运行在客户端的**脚本语言**。

脚本语言是指不需要编译，运行过程中由js解释器（js引擎）逐行来进行解释并执行。

#### 3. JavaScript的作用

表单动态校验（JS产生最初的目的）

网页特效

服务端开发(Node.js)

桌面程序(Electron)

App(Cordova) 

控制硬件-物联网(Ruff)

游戏开发(cocos2d-js)

#### 4. HTML、CSS、JS的关系

HTML、CSS是描述性语言，分别决定网页结构内容和网页模样。

JS是编程类语言，实现业务逻辑和页面控制。

#### 5. 浏览器执行JS简介

浏览器分为两部分：渲染引擎和JS引擎。

**渲染引擎**：用来解析HTML与CSS，俗称内核，比如 chrome 浏览器的 blink ，老版本的 webki。

**JS 引擎**：也称为 JS 解释器。 用来读取网页中的JavaScript代码，对其处理后运行，比如 chrome 浏览器的。

浏览器本身并不会执行JS代码，而是通过**内置 JavaScript 引擎**(解释器) 来执行 JS 代码 。JS 引擎执行代码时逐行解释 每一句源码（转换为机器语言），然后由计算机去执行，所以 JavaScript 语言归为脚本语言，会逐行解释执行。

#### 6. JS 的组成

<img src="https://img.zjgsuzjx.top/img/images/2021/06/18/d016c88db9ee46924c1f827d3919f792.png" alt="d016c88db9ee46924c1f827d3919f792.png" border="0" />

**1.ECMAScript**

ECMAScript 是由ECMA 国际（ 原欧洲计算机制造商协会）进行标准化的一门编程语言，这种语言在万维网上应用广 泛，它往往被称为 JavaScript 或 JScript，但实际上后两者是 ECMAScript 语言的实现和扩展。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/18/3d09e5544edc38e7c7905cbf2c60174c.png" alt="3d09e5544edc38e7c7905cbf2c60174c.png" border="0" />

ECMAScript：ECMAScript 规定了JS的编程语法和基础核心知识，是所有浏览器厂商共同遵守的一套JS语法工业标准。

**2.DOM ——文档对象模型**

文档对象模型（Document Object Model，简称DOM），是W3C组织推荐的处理可扩展标记语言的标准编程接口。 通过 DOM 提供的接口可以对页面上的各种元素进行操作（大小、位置、颜色等）。

**3.BOM ——浏览器对象模型**

BOM (Browser Object Model，简称BOM) 是指浏览器对象模型，它提供了独立于内容的、可以与浏览器窗口进行 互动的对象结构。通过BOM可以操作浏览器窗口，比如弹出框、控制浏览器跳转、获取分辨率等。

#### 7. JS 初体验

三种书写方式：行内、内嵌和外部。

**行内式JS**如：

```html
<input type="submit" value="click me" onclick="alert('hello world!')">
```

> 在HTML中我们推荐使用双引号, JS 中我们推荐使用单引号。

可读性差， 在html中编写JS大量代码时，不方便阅读。 特殊情况下使用。

**内嵌式的js**如：

```
<script>
    alert('helloworld!');
</script>
```

内嵌 JS 是学习时常用的方式。

**外部的JS**：

```
<script src="1-1.js"></script>
```

引用外部 JS文件的 script 标签中间不可以写代码。适合于JS 代码量比较大的情况。

### 二、JavaScript 注释

#### 1. 单行注释

```js
// 单行注释
```

快捷键：ctrl+/

#### 2. 多行注释

```js
/*多行
注释*/
```

快捷键：ctrl+shift+/

### 三、JavaScript 输入输出语句

```js
<script>
    alert('浏览器弹出警示框');
    prompt('浏览器弹出输入框');
    console.log('浏览器控制台打印输出内容');
</script>
```

## 二、变量

### 一、变量概述

#### 1. 概念

变量是用于存放数据的容器。 我们通过 变量名 获取数据，甚至数据可以修改。

#### 2. 变量在内存中的存储

本质：变量是程序在内存中申请的一块用来存放数据的空间。类似我们酒店的房间，一个房间就可以看做是一个变量。 

### 二、变量的使用

变量在使用时分为两步： 1. 声明变量 2. 赋值。

```javascript
<script>
    // 声明一个变量
    var age;
    // 赋值
    age=18;
    // 输出结果
    console.log(age);
    //或者直接声明赋值
    var mame1=18;
</script>
```

 **var** 是一个 JS关键字，用来声明变量( **variable** 变量的意思 )。使用该关键字声明变量后，计算机会自动为变量分配 内存空间，不需要程序员管。**=** 用来把右边的值赋给左边的变量空间中 此处代表赋值的意思。

**小案例**：

```js
<script>
    var myname=prompt('请输入你的名字：');
    alert(myname);
</script>
```

#### 1. 变量语法扩展

**更新变量**：

一个变量被重新复赋值后，它原有的值就会被覆盖，变量值将以最后一次赋的值为准。

```js
<script>
    var age = 18;
    age = 81; // 最后的结果就是81因为18 被覆盖掉了 
</script>
```

**同时声明多个变量**：

```js
var age = 10, name = 'zs', sex = 2;
```

同时声明多个变量时，只需要写一个 var，多个变量名之间使用英文逗号隔开。

**声明变量特殊情况**：

```js
<script>
    var age ; console.log (age); //只声明 不赋值 undefined
    console.log(age) //不声明 不赋值 直接使用 报错
    age = 10; console.log (age); //不声明 只赋值 10
</script>
```

### 三、变量命名规范

- 由字母(A-Za-z)、数字(0-9)、下划线(_)、美元符号( $ )组成，如：usrAge, num01, _name
- 严格区分大小写。var app; 和 var App; 是两个变量
- 不能 以数字开头。 18age 是错误的
- 不能 是关键字、保留字。例如：var、for、while
- 变量名必须有意义。 MMD BBD nl → age 
- 遵守**驼峰命名法**。首字母小写，后面单词的首字母需要大写。 **myFirstName**
- 推荐翻译网站： 有道 爱词霸

> 所谓保留字，就是浏览器中此变量可能已经由含义了，所谓不要去使用。

**交换两个变量的值**：

```js
<script>
    var pg1='no1',pg2='no2',tmp;
    tmp=pg1;
    pg1=pg2;
    pg2=tmp;
    console.log(pg1);
    console.log(pg2);
</script>
```

## 三、数据类型

### 一、数据类型简介

#### 1. 为什么需要数据类型

在计算机中，不同的数据所需占用的存储空间是不同的，为了便于把数据分成所需内存大小不同的数据，充分利 用存储空间，于是定义了不同的数据类型。简单来说，数据类型就是数据的类别型号。

#### 2. 变量的数据类型

JavaScript 是一种**弱类型**或者说**动态语言**。这意味着不用提前声明变量的类型，在程序运行过程中，类型会被自动确定。

```js
var age = 10; // 这是一个数字型
var areYouOk = '是的'; // 这是一个字符串 
```

在代码运行时，变量的数据类型是由 JS引擎 根据 **=** 右边变量值的数据类型来判断 的，运行完毕之后， 变量就确定了数据类型。

JavaScript 拥有**动态类型**，同时也意味着相同的变量可用作不同的类型：

```js
var x = 6; // x 为数字
var x = "Bill"; // x 为字符串 
```

#### 3. 数据类型的分类

JS 把数据类型分为两类：

- 简单数据类型 （Number,String,Boolean,Undefined,Null）
- 复杂数据类型 （object)

### 二、简单数据类型

#### 1. 简单数据类型（基本数据类型）

JavaScript 中的简单数据类型及其说明如下：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/18/6b92a6d24243003d9b4cc50eca216d8c.png" alt="6b92a6d24243003d9b4cc50eca216d8c.png" border="0" />

#### 2. 数字型 Numb

**数字型进制**：

最常见的进制有二进制、八进制、十进制、十六进制。

```js
// 1.八进制数字序列范围：0~7
var num1 = 07; // 对应十进制的7
var num2 = 019; // 对应十进制的19
var num3 = 08; // 对应十进制的8
// 2.十六进制数字序列范围：0~9以及A~F
var num = 0xA;
```

现阶段我们只需要记住，在JS中八进制前面加0，十六进制前面加 0x 。

**数字型范围**：

JavaScript中数值的最大和最小值

```js
alert(Number.MAX_VALUE); // 1.7976931348623157e+308
alert(Number.MIN_VALUE); // 5e-324
```

**数字型三个特殊值**：

```js
alert(Infinity); // Infinity
alert(-Infinity); // -Infinity
alert(NaN); // NaN
```

- Infinity ，代表无穷大，大于任何数值
- -Infinity ，代表无穷小，小于任何数值
- NaN ，Not a number，代表一个非数值

**isNaN()**：

```js
console.log('pink') //true
console.log(11) //false
```

#### 3. 字符串型 String

字符串型可以是引号中的任意文本，其语法为 双引号 "" 和 单引号''

```js
var strMsg = "我爱北京天安门~"; // 使用双引号表示字符串
var strMsg2 = '我爱吃猪蹄~'; // 使用单引号表示字符串
// 常见错误
var strMsg3 = 我爱大肘子; // 报错，没使用引号，会被认为是js代码，但js没有这些语法
```

> JS 这里我们更推荐使用单引号。

 **字符串引号嵌套**：

JS 可以用单引号嵌套双引号 ，或者用双引号嵌套单引号 (**外双内单**，**外单内双**）。

```js
var strMsg = '我是"高帅富"程序猿'; // 可以用''包含""
var strMsg2 = "我是'高帅富'程序猿"; // 也可以用"" 包含'' 
// 常见错误
var badQuotes = 'What on earth?"; // 报错，不能 单双引号搭
```

**字符串转义符**：

转义符都是 \ 开头的，常用的转义符及其说明如下：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/18/bec4ed211fccfc0f1408f8a7c010ad6e.png" alt="bec4ed211fccfc0f1408f8a7c010ad6e.png" border="0" />

**字符串长度**：

通过字符串的 length 属性可以获取整个字符 串的长度。

```js
var strMsg = "我是帅气多金的程序猿！";
alert(strMsg.length); // 显示 11
```

**字符串拼接**：

多个字符串之间可以使用 + 进行拼接，其拼接方式为 字符串 **+** 任何类型 = 拼接之后的新字符串。

```js
//1.1 字符串 "相加" 
alert('hello' + ' ' + 'world'); // hello world
//1.2 数值字符串 "相加" 
alert('100' + '100'); // 100100
//1.3 数值字符串 + 数值
alert('11' + 12); // 1112
alert(11+11+'11' + 12 + 11); // 22111211
```

> \+ 号总结口诀：数值相加 ，字符相连。

**字符串拼接加强**：

```js
console.log('pink老师' + 18); // 只要有字符就会相连
var age = 18;
console.log('pink老师age岁啦'); // 错误
console.log('pink老师' + age); // pink老师18
console.log('pink老师' + age + '岁啦'); // pink老师18岁啦
```

> 如果变量两侧都有字符串拼接，口诀“引引加加 ”，删掉数字，变量写加中间。

**简单的交互案例**：

```js
var name1 = prompt('您是？');
var str = '欢迎' + name1;
alert(str);
```

#### 4. 布尔型 Boolean

布尔类型有两个值：**true** 和 **false** ，其中 true 表示真（对），而 false 表示假（错）。 

布尔型和数字型相加的时候， true 的值为 **1** ，false 的值为 **0**。

```js
console.log(true + 1); // 2
console.log(false + 1); // 1
```

#### 5. Undefined 和 Null

一个声明后没有被赋值的变量会有一个**默认值** undefined ( 如果进行相连或者相加时，注意结果）

```js
var variable;
console.log(variable); // undefined
console.log('你好' + variable); // 你好undefined
console.log(11 + variable); // NaN
console.log(true + variable); // NaN
```

一个声明变量给 null 值，里面存的值为**空**（学习对象时，我们继续研究null)

```js
var vari = null;
console.log('你好' + vari); // 你好null
console.log(11 + vari); // 11
console.log(true + vari); // 1
```

> 注意undefined 和 null 和数字相加结果不一样。

### 三、获取变量数据类型

#### 1. 获取检测变量的数据类型

typeof 可用来获取检测变量的数据类型。

```js
var num = 18;
        console.log(typeof num) // 结果 number
        var str = '18';
        console.log(typeof str) // 结果 string
        var flag = true;
        console.log(typeof flag) // 结果 boolean
        var vari = undefined;
        console.log(typeof vari) // 结果 undefined
        var timer = null;
        console.log(typeof timer) // 结果 object
```

> 另外可以通过浏览器命令台的输出颜色来判断是什么数据类型

#### 2. 字面量

字面量是在源代码中一个固定值的表示法，通俗来说，就是字面量表示如何表达这个值。

- 数字字面量：8, 9, 10
- 字符串字面量：'黑马程序员', "大前端"
- 布尔字面量：true，false

### 四、数据类型转换

#### 1. 什么是数据类型转换

使用表单、prompt 获取过来的数据默认是**字符串类型**的，此时就不能直接简单的进行加法运算，而需要转换变量的数据类型。通俗来说，就是把一种数据类型的变量转换成另外一种数据类型。

我们通常会实现3种方式的转换：

- 转换为字符串类型
- 转换为数字型
- 转换为布尔型

#### 2. 转换为字符串

```js
var num = 10;
//利用变量.toString()
var str = num.toString();
// 利用String(变量)
console.log(String(num));
// 利用 + 拼接字符串的方法实现转换效果
console.log(num + '');
```

三种转换方式，我们更喜欢用第三种加号拼接字符串转换方式， 这一种方式也称之为**隐式转换**。

#### 3. 转换为数字型

```js
var age = prompt();
//将字符串转整型
console.log(parseInt(age));
console.log(parseInt('120px'));//120 会去掉px
console.log(parseInt('2.94'));//2 向下取整
//将字符串转浮点数
console.log(parseFloat(age));
//利用Number(变量)
var str = '12';
console.log(Number(age));
//利用js隐式转换 - / *
console.log('11' - 0);
console.log('11' * 1);
```

注意 **parseInt** 和 **parseFloat** 单词的大小写，这2个是重点。

**隐式转换**是我们在进行算数运算的时候，JS 自动转换了数据类型。

**计算年龄案例**：

```js
var year = prompt("请输入出生年份：");
var age = 2021 - year;//js隐式转换
alert('您今年已经' + age + '岁了');
```

#### 4. 转换为布尔型

```js
console.log(Boolean('')); // false
console.log(Boolean(0)); // false
console.log(Boolean(NaN)); // false
console.log(Boolean(null)); // false
console.log(Boolean(undefined)); // false
console.log(Boolean('小白')); // true
console.log(Boolean(12)); // true
```

代表空、否定的值会被转换为 false ，如 ''、0、NaN、null、undefined 。其余值都会被转换为 true。

## 三、扩展阅读

### 一、解释型语言和编译型语言

#### 1. 概述

翻译器翻译的方式有两种：一个是**编译**，另外一个是**解释**。两种方式之间的区别在于翻译的**时间点**不同。

编译器是在<u>代码执行之前</u>进行编译，生成中间代码文件。

解释器是在<u>运行时进行及时解释</u>，并立即执行(当编译器以解释方式运行的时候，也称之为解释器)。

#### 2. 执行过程

<img src="https://img.zjgsuzjx.top/img/images/2021/06/18/f2b6a6341c3e1a5c078f42467d29fb48.png" alt="f2b6a6341c3e1a5c078f42467d29fb48.png" border="0" />

### 二、标识符、关键字、保留字

#### 1. 标识符

就是指开发人员为变量、属性、函数、参数取的**名字**。 标识符不能是关键字或保留字。

#### 2. 关键字

关键字是指 JS本身已经使用了的字，不能再用它们充当变量名、方法名。 

包括：break、case、catch、continue、default、delete、do、else、finally、for、function、if、in、 instanceof、new、return、switch、this、throw、try、typeof、var、void、while、with 等。

#### 3. 保留字

保留字：实际上就是<u>预留的“关键字”</u>，意思是现在虽然还不是关键字，但是未来可能会成为关键字，同样不能使用它们当变量名或方法名。

包括：boolean、byte、char、class、const、debugger、double、enum、export、extends、 fimal、float、goto、implements、import、int、interface、long、mative、package、 private、protected、public、short、static、super、synchronized、throws、transient、 volatile 等。

> 注意：如果将保留字用作变量名或函数名，那么除非将来的浏览器实现了该保留字，否则很可能收不到任何错误消息。当浏览器将其实现后，该单词将被看做关键字，如此将出现关键字错误。

## 四、JavaScript 运算符

### 一、运算符

运算符（operator）也被称为**操作符**，是用于实现赋值、比较和执行算数运算等功能的符号。

### 二、算数运算符

#### 1. 算术运算符概述

**概念**：算术运算使用的符号，用于执行两个变量或值的算术运算。

加+、减-、乘*、除/、取余数（取模）%

#### 2. 浮点数的精度问题

```js
var result = 0.1 + 0.2; // 结果不是 0.3，而是：0.30000000000000004
console.log(0.07 * 100); // 结果不是 7， 而是：7.000000000000001
```

```js
var num = 0.1 + 0.2;
console.log(num == 0.3) //false
```

> 所以：不要直接判断两个浮点数是否相等 !

#### 3. 表达式和返回值

**表达式**：是由数字、运算符、变量等以能求得数值的有意义排列方法所得的组合

简单理解：是由数字、运算符、变量等组成的式子.

表达式最终都会有一个结果，返回给我们，我们成为**返回值**

### 三、递增和递减运算符

#### 1. 概述

如果需要反复给数字变量添加或减去1，可以使用递增（**++**）和递减（ **--** ）运算符来完成。

在 JavaScript 中，递增（++）和递减（ -- ）既可以放在变量**前面**，也可以放在变量**后面**。放在变量前面时， 我们可以称为**前置递增**（递减）运算符，放在变量后面时，我们可以称为**后置递增**（递减）运算符。

> 注意：递增和递减运算符必须和**变量**配合使用。

#### 2. 递增运算符

**前置递增运算符**：++num 前置递增，就是自加1，类似于 num = num + 1，但是 ++num 写起来更简单。

> 使用口诀：先自加，后返回值。与C++相同。

```js
var num = 10;
alert(++num + 10); // 21
```

**后置递增运算符**：

num++ 后置递增，就是自加1，类似于 num = num + 1 ，但是 num++ 写起来更简单。

> 使用口诀：先返回原值，后自加。与C++相同。

```js
var num = 10;
alert(10 + num++); // 20
```

#### 3. 小结

- 前置递增和后置递增运算符可以简化代码的编写，让变量的值 + 1 比以前写法更简单
- 单独使用时，运行结果相同
- 与其他代码联用时，执行结果会不同
- 后置：先原值运算，后自加（**先人后己**）
- 前置：先自加，后运算（**先已后人**）
- 开发时，大多使用**后置递增/减**，并且代码独占一行，例如：num++; 或者 num--;

### 四、比较运算符

#### 1. 概述

比较运算符（关系运算符）是两个数据进行比较时所使用的运算符，比较运算后，会返回一个**布尔值** （true / false）作为比较运算的结果。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/c2f1e4944bb3a8db7b6648dc7bbc1377.png" alt="c2f1e4944bb3a8db7b6648dc7bbc1377.png" border="0" />

```js
console.log(18 == '18') //true 会自动转型
console.log(18 === '18') //要求值和数据类型完全一致
```

#### 2. =小结

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/7c59ca8b6bfd4f9aee816e632dda3d2a.png" alt="7c59ca8b6bfd4f9aee816e632dda3d2a.png" border="0" />

### 五、逻辑运算符

#### 1. 概念

逻辑运算符是用来进行布尔值运算的运算符，其返回值也是布尔值。后面开发中经常用于多个条件的判断。

```js
console.log(3 > 5 && 3 > 2); //只要一个是假，false
console.log(3 < 5 && 3 > 2); //全部是真，true
console.log(3 > 5 || 3 > 2); //只要一个是真，true
console.log(3 < 5 ||3 > 2); //全部是假，false
```

#### 2. 逻辑非 ！

逻辑非（**!**）也叫作**取反符**，用来取一个布尔值相反的值，如 true 的相反值是 false

```js
var isOk = !true;
console.log(isOk); // false
```

#### 3. 短路运算（逻辑中断）

短路运算的**原理**：当有多个**表达式**（值）时,左边的表达式值可以确定结果时,就不再继续运算右边的表达式的值。

**逻辑与**：

- 语法： 表达式1 && 表达式2
- 如果第一个表达式的值为真，则返回表达式2
- 如果第一个表达式的值为假，则返回表达式1

```js
console.log( 123 && 456 ); // 456
console.log( 0 && 456 ); // 0
console.log( 123 && 456&& 789 ); // 789
```

**逻辑或**：

- 语法： 表达式1 || 表达式2
- 如果第一个表达式的值为真，则返回表达式1
- 如果第一个表达式的值为假，则返回表达式2

```js
console.log( 123 || 456 ); // 123
console.log( 0 || 456 ); // 456
console.log( 123 || 456 || 789 ); // 123
```

```js
var num = 0;
console.log(123 || num++);
console.log(num); //结果是0
```

> 注意在表达式有自增/减的情况。逻辑中断会影响程序运行结果。

### 六、赋值运算符

**概念**：用来把数据赋值给变量的运算符。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/dd1d647235b05c333fa4fffea7de8c2c.png" alt="dd1d647235b05c333fa4fffea7de8c2c.png" border="0" />

```js
var age = 10;
age += 5; // 相当于 age = age + 5;
age -= 5; // 相当于 age = age - 5;
age *= 10; // 相当于 age = age * 10;
```

### 七、运算符优先级

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/6da1d3c3d50f6a6a4c728f9aba78aaa0.png" alt="6da1d3c3d50f6a6a4c728f9aba78aaa0.png" border="0" />

- 一元运算符里面的逻辑非优先级很高
- 逻辑与比逻辑或优先级高

## 五、JavaScript 流程控制-分支

### 一、流程控制

在一个程序执行的过程中，各条代码的执行顺序对程序的结果是有直接影响的。很多时候我们要通过控制代码 的执行顺序来实现我们要完成的功能。

> 简单理解： 流程控制就是来控制我们的代码按照什么结构顺序来执行

流程控制主要有三种结构，分别是**顺序结构**、**分支结构**和**循环结构**，这三种结构代表三种代码执行的顺序。

### 二、顺序流程控制

顺序结构是程序中最简单、最基本的流程控制，它没有特定的语法结构，程序会按照代码的<u>先后顺序，依次执行</u>，程序中大多数的代码都是这样执行的。

### 三、分支流程控制 if 语句

#### 1. 分支结构

由上到下执行代码的过程中，根据不同的条件，执行不同的路径代码（执行代码**多选一**的过程），从而得到不同的结果。

JS 语言提供了两种分支结构语句

- if 语句
- switch 语句

#### 2.  if 语句

**语法结构**：

```js
// 条件成立执行代码，否则什么也不做
if (条件表达式) {
    // 条件成立执行的代码语句
}
```

**执行流程**:

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/14da781995828ba2104013c73123cf5c.png" alt="14da781995828ba2104013c73123cf5c.png" border="0" />

**例子**：

```js
var usrAge = prompt('请输入您的年龄：');
if(usrAge >= 18){
    alert('您的年龄合法，欢迎来天际网吧享受学习的乐趣！');
}
```

#### 3. if else语句（双分支语句）

**语法结构**：

```js
// 条件成立 执行 if 里面代码，否则执行else 里面的代码
if (条件表达式) {
    // [如果] 条件成立执行的代码
} else {
    // [否则] 执行的代码
}
```

**执行流程**：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/743e171c4f3240f41fa74fee8e20838b.jpg" alt="743e171c4f3240f41fa74fee8e20838b.jpg" border="0" />

**判断闰年案例**：

```js
var year = prompt('请输入年份：');
if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
    alert("这个年份是闰年");
} else { // 剩下的是平年
    alert("这个年份是平年");
}
```

#### 4. if else if 语句(多分支语句)

**语法结构**：

```js
// 适合于检查多重条件。
if (条件表达式1) {
    语句1；
} else if (条件表达式2) {
    语句2；
} else if (条件表达式3) {
    语句3；
....
} else {
    // 上述条件都不成立执行此处代码
}
```

**执行流程**：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/1dd12629ede0b90857175726c9633308.png" alt="1dd12629ede0b90857175726c9633308.png" border="0" />

**判断成绩级别案例**：

```js
var score = prompt('请您输入分数:');
if (score >= 90) {
    alert('宝贝，你是我的骄傲');
} else if (score >= 80) {
    alert('宝贝，你已经很出色了');
} else if (score >= 70) {
    alert('你要继续加油喽');
} else if (score >= 60) {
    alert('孩子，你很危险');
} else {
    alert('熊孩子，我不想和你说话');
}
```

> 注意：按照从大到小判断的思路

### 四、三元表达式

三元表达式也能做一些简单的条件选择。 有三元运算符组成的式子称为三元表达式。

#### 1. 语法结构

```js
表达式1 ? 表达式2 : 表达式3;
```

#### 2. 执行思路

如果表达式1为 **true** ，则返回表达式2的值，如果表达式1为 **false**，则返回表达式3的值

> 简单理解： 就类似于 if else（双分支）的简写

**数字补0案例**：

```js
var time = prompt('请您输入一个 0 ~ 59 之间的一个数字');
// 三元表达式 表达式 ？ 表达式1 ：表达式2 
var result = time < 10 ? '0' + time : time; // 把返回值赋值给一个变量
alert(result);
```

### 五、分支流程控制 switch 语句

#### 1. 语法结构

switch 语句也是多分支语句，它用于基于不同的条件来执行不同的代码。当要针对变量设置一系列的特定值 的选项时，就可以使用 switch。

```js
switch( 表达式 ){
    case value1:
        // 表达式 等于 value1 时要执行的代码
        break;
    case value2:
        // 表达式 等于 value2 时要执行的代码
        break;
    default:
    // 表达式 不等于任何一个 value 时要执行的代码
}
```

- switch ：开关/转换，case ：小例子/选项
- 关键字 switch 后面**括号内**可以是**表达式**或**值**， 通常是一个**变量**
- 关键字 **case** , 后跟一个选项的**表达式**或**值**，后面跟一个冒号
- switch 表达式的值会与结构中的 case 的值做比较
- 如果存在匹配全等(===) ，则与该 case 关联的代码块会被执行，并在遇到 **break** 时停止，整个 switch 语句代码 执行结束
- 如果所有的 case 的值都和表达式的值不匹配，则执行 **default** 里的代

> 注意： 执行case 里面的语句时，如果没有break，则继续执行下一个case里面的语句。没有一直没有break，会执行到最后一行。

#### 2. switch 语句和 if else if 语句的区别

① 一般情况下，它们两个语句可以相互替换

② switch...case 语句通常处理 case为比较**确定值**的情况， 而 if…else…语句更加灵活，常用于**范围**判断(大于、 等于某个范围)

③ switch 语句进行条件判断后**直接执行**到程序的条件语句，效率更高。而if…else 语句有几种条件，就得判断多少次。

④ 当分支比较**少**时，if… else语句的**执行效率**比 switch语句**高**。

⑤ 当分支比较**多**时，switch语句的执行效率比较高，而且结构更清晰。

## 六、JavaScript 流程控制-循环

### 一、循环

**循环目的**：

在实际问题中，有许多具有**规律性**的重复操作，因此在程序中要完成这类操作就需要重复执行某些语句。

在Js 中，主要有三种类型的循环语句：

for 循环、while 循环、 do...while 循环

### 二、for 循环

在程序中，一组被重复执行的语句被称之为**循环体**，能否继续重复执行，取决于循环的**终止条件**。由循环体 及循环的终止条件组成的语句，被称之为**循环语句**

#### 1. 语法结构

```js
for(初始化变量; 条件表达式; 操作表达式 ){
    //循环体
}
```

**初始化变量**：通常被用于初始化一个计数器，该表达式可以使用 var 关键字声明新的变量，这个变量帮我们来记录次数。

**条件表达式**：用于确定每一次循环是否能被执行。如果结果是 true 就继续循环，否则退出循环。

**操作表达式**：每次循环的最后都要执行的表达式。通常被用于更新或者递增计数器变量。当然，递减变量也是可以的。

#### 2. 执行过程

1. 初始化变量，初始化操作在整个 for 循环只会执行一次。
2. 执行条件表达式，如果为true，则执行循环体语句，否则退出循环，循环结束。
3. 执行操作表达式，此时第一轮结束。
4. 第二轮开始，直接去执行条件表达式（不再初始化变量），如果为 true ，则去执行循环体语句，否则退出循环。
5. 继续执行操作表达式，第二轮结束。
6. 后续跟第二轮一致，直至条件表达式为假，结束整个 for 循环。

#### 3. 断点调试

断点调试是指自己在程序的某一行设置一个断点，调试时，程序运行到这一行就会停住，然后你可以一步一步往下调试，调试过程中可以看各个变量当前的值，出错的话，调试到出错的代码行即显示错误，停下。

> 断点调试可以帮我们观察程序的运行过程

浏览器中按 F12--> sources -->找到需要调试的文件-->在程序的某一行设置断点

Watch: 监视，通过watch可以监视变量的值的变化，非常的常用。

F11: 程序单步执行，让程序一行一行的执行，这个时候，观察watch中变量的值的变化。

#### 4. for 循环重复相同的代码

```js
// 基本写法
for (var i = 1; i <= 10; i++) {
    console.log('媳妇我错了~');
}
// 用户输入次数
var num = prompt('请输入次数:');
for (var i = 1; i <= num; i++) {
    console.log('媳妇我错了~');
}
```

#### 5. for 循环重复不相同的代码

```js
// for 里面是可以添加其他语句的
for (var i = 1; i <= 100; i++) {
    if (i == 1) {
        console.log('这个人今年1岁了， 它出生了');
    } else if (i == 100) {
        console.log('这个人今年100岁了，它死了');
    } else {
        console.log('这个人今年' + i + '岁了');
    }
}
```

**累加和案例**：

```js
var sum = 0;
for(var i = 1;i <= 100; i++){
    sumNum += i;
}
console.log('1-100之间整数的和 = ' + sum);
```

**求学生成绩案例**：

```js
var num = prompt('请输入班级总的人数:'); // num 班级总的人数
var sum = 0; // 总成绩
var average = 0; // 平均成绩
for (var i = 1; i <= num; i++) {
    var score = prompt('请输入第' + i + '个学生的成绩');
    sum = sum + parseFloat(score);
}
average = sum / num;
alert('班级总的成绩是：' + sum);
alert('班级总的平均成绩是：' + average);
```

### 三、双重 for 循环

#### 1. 概述

循环嵌套是指在一个循环语句中再定义一个循环语句的语法结构，例如在for循环语句中，可以再嵌套一个 for 循环，我们称之为**双重for循环**。

#### 2. 语法

```js
for (外循环的初始; 外循环的条件; 外循环的操作表达式) {
    for (内循环的初始; 内循环的条件; 内循环的操作表达式) {
        需执行的代码;
    }
}
```

**打印n行n列的星星**：

```js
var row = prompt('请输入您打印几行星星:');
var col = prompt('请输入您打印几列星星:');
var str = '';
for (var i = 1; i <= row; i++) {
    for (j = 1; j <= col; j++) {
        str += '☆';
    }
    str += '\n';
}
console.log(str);
```

**打印倒三角形**：

```javascript
var row = prompt('请输入您打印几行星星:');
var col = prompt('请输入您打印几列星星:');
var str = '';
for (var i = 1; i <= row; i++) {
    for (j = i; j <= col; j++) {
        str += '☆';
    }
    str += '\n';
}
console.log(str);
```

**打印九九乘法表**：

```js
var str = ''
for (var i = 1; i <= 9; i++) { // 外层for控制 行数 9行
    for (var j = 1; j <= i; j++) { // j 控制列数 列数和行数是一样的 j <= i
        str += j + " × " + i + " = " + i * j + '\t';
    }
    str += '\n';
}
console.log(str);
```

#### 3. 小结

- for 循环可以重复执行某些相同代码
- for 循环可以重复执行些许不同的代码，因为我们有计数器
- for 循环可以重复执行某些操作，比如算术运算符加法操作
- 双重 for 循环，外层循环一次，内层 for 循环全部执行
- for 循环是循环条件和数字直接相关的循环

### 四、while 循环

while 语句可以在条件表达式为真的前提下，循环执行指定的一段代码，直到表达式不为真时结束循环。

#### 1. 语法

```js
while (条件表达式) {
    // 循环体代码
}
```

#### 2. 执行思路

① 先执行条件表达式，如果结果为 **true**，则执行循环体代码；如果为 **false**，则退出循环，执行后面代码

② 执行循环体代码

③ 循环体代码执行完毕后，程序会继续判断执行条件表达式，如条件仍为true，则会继续执行循环体，直到循环条件为 false 时，整个循环过程才会结束

**注意**：

① 使用 while 循环时一定要注意，它必须要有退出条件，否则会成为**死循环**

② while 循环和 for 循环的不同之处在于 while 循环可以做较为复杂的条件判断，比如判断用户名和密码

**案例**：

```js
var str = prompt('你爱我吗？');
while(str !== '我爱你'){
    str = prompt('你爱我吗？');
}
alert('我也爱你');
```

### 五、do while 循环

#### 1. 语法

```js
do {
    // 循环体代码 - 条件表达式为 true 时重复执行循环体代码
} while(条件表达式);
```

#### 2. 执行思路

① 先执行一次循环体代码

② 再执行条件表达式，如果结果为 true，则继续执行循环体代码，如果为 false，则退出循环，继续执行后面代码

> 注意：先再执行循环体，再判断，我们会发现 do…while 循环语句至少会执行**一次**循环体代码

#### 3. 循环小结

- JS 中循环有 for 、while 、 do while 
- 三个循环很多情况下都可以相互替代使用
- 如果是用来计次数，跟数字相关的，三者使用基本相同，但是我们更喜欢用 **for**
- while 和 do…while 可以做更**复杂**的判断条件，比 for 循环灵活一些
- while 和 do…while **执行顺序**不一样，while 先判断后执行，do…while 先执行一次，再判断执行
- while 和 do…while 执行次数不一样，do…while **至少**会执行一次循环体， 而 while 可能一次也不执行
- 实际工作中，我们更常用**for**循环语句，它写法更简洁直观， 所以这个要重点学

### 六、continue break

#### 1. continue 关键字

continue 关键字用于立即**跳出本次**循环，继续**下一次**循环（本次循环体中 continue 之后的代码就会少执行一次）。

```js
for (var i = 1; i <= 5; i++) {
    if (i == 3) {
        console.log('这个包子有虫子，扔掉');
        continue; // 跳出本次循环，跳出的是第3次循环
    }
    console.log('我正在吃第' + i + '个包子呢');
}
```

#### 2. break 关键字

break 关键字用于立即**跳出整个**循环（循环结束）。

```js
for (var i = 1; i <= 5; i++) {
    if (i == 3) {
        break; // 直接退出整个for 循环，跳到整个for下面的语句
    }
    console.log('我正在吃第' + i + '个包子呢');
}
```

### 七、JavaScript命名规范

#### 1. 标识符命名规范

- 变量、函数的命名不许要有意义
- 变量的名称一般用**名词**
- 函数的名称一般用**动词**

#### 2. 操作符规范

操作符两边要有空格。

#### 3. 单行注释规范

单行注释前面注意有个空格。

#### 4. 其它规范

**if**、**for**等关键字和**(**要有一个空格，**)**和**{**之间也要有一个空格。

**ATM取款机案例**：

```js
// ATM取款机
var str = '请输入您要的操作：\n1.存钱\n2.取钱\n3.显示余额\n4.退出';
var money = 100,op;
do {
    op = prompt(str);
    switch (op) {
        case '1':
            var takem = prompt('请输入存的钱数：');
            money += parseFloat(takem);
            break;
        case '2':
            var putm = prompt('请输入取钱数：');
            money -= parseFloat(putm);
            break;
        case '3':
            alert('你现在有' + money + '元');
            break;
        case '4':
            break;
    }
} while (parseInt(op) != 4);
alert('感谢您的使用！');
```

## 七、JavaScript数组

### 一、概念

数组可以把一组相关的数据一起存放，并提供方便的访问（获取）方式。

数组是指一组**数据**的集合，其中的每个数据被称作**元素**，在数组中可以存放任意类型的元素。数组是一种将一组数据存储在单个变量名下的优雅方式。

### 二、创建数组

JS中创建数组有两种方式：

- 利用new创建数组
- 利用数组字面量创建数组

```js
var arr = new Array(); // new创建数组
```

#### 1. 数组字面量创建数组

```js
var arr = [1, 2, '3', true];
```

- 数组的字面量是方括号[]
- 声明数组并赋值称为数组的初始化
- 这种字面量方式也是我们以后**最多**使用的方式

#### 2. 数组的数据类型

数组中可以存放**任意类型**的数据，例如字符串，数字，布尔值等。

### 三、获取数组的元素

#### 1. 数组的索引

**索引**（下标）：用来访问数组元素的序号（数组下标从**0**开始）。

数组可以通过**索引**来访问、设置、修改对应的数组元素，我们可以通过“**数组名[索引]**”的形式来获取数组中的元素，这里的**访问**就是获取得到的意思。

```js
var arr = [1, 2, 3];
alert(arr[0]);
alert(arr[3]);// 输出undefined
```

### 四、遍历数组

**遍历**：就是把数组中的每个元素从头到尾都访问一次。

```js
var arr = [1, 2, 3];
for (var i = 0; i < 3; i++) {
    console.log(arr[i]);
}
```

#### 1. 数组的长度

使用“数组名.length”可以访问数组元素的数量（数组长度）。

```js
for (var i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

**求和案例**：

```js
var arr = [2, 6, 1, 7, 4];
var sum = 0;
var average = 0;
for (var i = 0; i < arr.length; i++) {
    sum += arr[i];//我们加的是数组元素arr[i]不是计数器i 
}
average = sum / arr.length;
console.log(sum, average);
```

**数组转换字符串**：

```js
var arr = ['red', 'green', 'blue'];
var str = '';
var sep = '|';
for (var i = 0; i < arr.length; i++) {
    str += arr[i] + sep;
}
console.log(str);
```

### 五、数组中新增元素

#### 1. 通过修改 length 长度

- 可以通过修改length长度来实现数组扩容的目的
- length属性是可读写的

```js
var arr = ['red', 'green', 'blue'];
arr.length = 5;
console.log(arr[3]); // undefined
```

#### 2. 通过修改数组索引

- 可以通过修改数组索引的方式追加数组元素。

```js
var arr = ['red', 'green', 'blue'];
arr[3] = 'pink';// 追加元素
console.log(arr);
arr[0] = 'pink';// 替换元素
arr = 'pink';// 数组元素全被覆盖
```

**筛选数组**：

```js
var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
var newArr = [];
var j = 0;
for (var i = 0; i < arr.length; i++) {
    if (arr[i] >= 10) {
        //新数组索引号应该从e开始依次递增
        newArr[newArr.length] = arr[i];
        j++;
    }
}
console.log(newArr);
```

## 八、JavaScript 函数

### 一、概念

**函数**：就是封装了一段可被**重复**调用执行的代码块。通过此代码块可以实现大量代码的重复使用。

### 二、函数的使用

#### 1. 声明函数

```js
// 声明函数
function 函数名() {
    //函数体代码
}
```

> function 是声明函数的**关键字**,必须**小写**

由于函数一般是为了实现某个功能才定义的， 所以通常我们将**函数名**命名为**动词**，比如 getSum

#### 2. 调用函数

```js
// 调用函数
函数名(); // 通过调用函数名来执行函数体代码
```

调用的时候千万不要忘记添加**小括号**

口诀：函数不调用，自己不执行。

> 注意：声明函数本身并不会执行代码，只有调用函数时才会执行函数体代码

#### 3. 函数的封装

函数的封装是把一个或者多个功能通过函数的方式**封装**起来，对外只提供一个简单的函数接口

> 简单理解：封装类似于将电脑配件整合组装到机箱中 ( 类似快递打包）

**累加和案例**：

```js
// 声明函数
function getSum() {
    var sumNum = 0;// 准备一个变量，保存数字和
    for (var i = 1; i <= 100; i++) {
        sumNum += i;// 把每个数值 都累加 到变量中
    }
    alert(sumNum);
}
// 调用函数
getSum();
```

### 三、函数的参数

#### 1. 形参和实参

在**声明函数**时，可以在函数名称后面的小括号中添加一些参数，这些参数被称为**形参**，而在调用该函数时， 同样也需要传递相应的参数，这些参数被称为**实参**。

**形参**：形式上的参数，函数定义的时候传递的参数，当前并不知道是什么
**实参**：实际上的参数，函数调用的时候传递的参数，实参是传递给形参的

**参数的作用** : 在函数内部某些值不能固定，我们可以通过参数在调用函数时传递不同的值进去。

```js
// 带参数的函数声明
function 函数名(形参1, 形参2 , 形参3...) { // 可以定义任意多的参数，用逗号分隔
    // 函数体
}
// 带参数的函数调用
函数名(实参1, 实参2, 实参3...);
```

#### 2. 函数参数的传递过程

```js
// 声明函数
function getSum(num1, num2) {
    console.log(num1 + num2);
}
// 调用函数
getSum(1, 3); // 4
getSum(6, 5); // 11
```

1. 调用的时候实参值是**传递**给形参的

2. 形参简单理解为：**不用声明**的变量
3. 实参和形参的多个参数之间用逗号（**,**）分隔

#### 3. 形参和实参个数的不匹配

实参个数**等于**形参个数：输出正确结果

实参个数**多于**形参个数：只取到形参的个数

实参个数**小于**形参个数：多的形参定义为**undefined**，结果为**NaN**

```js
function sum(num1, num2) {
    console.log(num1 + num2);
}
sum(100, 200); // 形参和实参个数相等，输出正确结果
sum(100, 400, 500, 700); // 实参个数多于形参，只取到形参的个数
sum(200); // 实参个数少于形参，多的形参定义为undefined，结果为NaN
```

> 注意：在JavaScript中，形参的默认值是undefined。

#### 4. 小结

- 函数可以带参数也可以**不带参数**
- 声明函数的时候，函数名括号里面的是形参，形参的默认值为 **undefined**
- 调用函数的时候，函数名括号里面的是实参
- 多个参数中间用**逗号**分隔
- 形参的个数可以和实参个数不匹配，但是结果**不可预计**，我们尽量要匹配

### 四、函数的返回值

#### 1. return 语句

有的时候，我们会希望函数将值返回给调用者，此时通过使用 **return** 语句就可以实现。

```js
// 声明函数
function 函数名 () {
...
    return 需要返回的值；
}
// 调用函数
函数名(); // 此时调用函数就可以得到函数体内return 后面的值
```

在使用 **return** 语句时，函数会**停止**执行，并返回指定的值

如果函数没有 **return** ，返回的值是 **undefined**

**求任意两个数的最大值**：

```js
function getMax(num1, num2) {
    return num1 > num2 ? num1 : num2;
}
console.log(getMax(1, 2));
console.log(getMax(11, 2));
```

**求任意一个数组中的最大值**：

```js
//定义一个获取数组中最大数的函数
function getMaxFromArr(numArray){
    var maxNum = 0;
    for(var i =0;i < numArray.length;i++){
        if(numArray[i] > maxNum){
            maxNum = numArray[i];
        }
    }
    return maxNum;
}
var arrNum = [5,2,99,101,67,77];
var maxN = getMaxFromArr(arrNum); // 这个实参是个数组
alert('最大值为：'+ maxN);
```

#### 2. return 终止函数

> **return** 语句之后的代码不被执行。

```js
function add(num1, num2){
    //函数体
    return num1 + num2; // 注意：return 后的代码不执行
    alert('我不会被执行，因为前面有 return');
}
var resNum = add(21,6); // 调用函数，传入两个实参，并通过 resNum 接收函数返回值
alert(resNum); // 27
```

#### 3. return 的返回值

> return 只能返回**一个值**。如果用逗号隔开多个值，以**最后一个**为准。

```js
function add(num1，num2){
    //函数体
    return num1，num2;
}
var resNum = add(21,6); // 调用函数，传入两个实参，并通过 resNum 接收函数返回值
alert(resNum); // 6
```

**返回数组案例**：

```js
var a = parseFloat(prompt('请输入第一个数'));
var b = parseFloat(prompt('请输入第二个数'));
function count(a, b) {
    var arr = [a + b, a - b, a * b, a / b];
    return arr;
}
var result = count(a, b); //返回数组
console.log(result);
```

#### 4. 没有 return 返回 undefined

函数都是有返回值的

1. 如果有**return** 则返回 **return** 后面的值
2. 如果没有**return** 则返回 **undefine**

```js
function fun1() {
    return; //和不写一样，都是undefined
}
console.log(fun1());
```

#### 5. break ,continue ,return 的区别

- break ：结束当前的循环体（如 for、while）
- continue ：跳出本次循环，继续执行下次循环（如 for、while）
- return ：不仅可以退出循环，还能够返回 return 语句中的值，同时还可以结束当前的函数体内的代码

### 五、arguments的使用

当我们不确定有多少个参数传递的时候，可以用 **arguments** 来获取。在 JavaScript 中，arguments 实际上 它是当前函数的一个**内置对象**。

> 所有函数都内置了一个 arguments 对象，arguments 对象中存储了**传递的所有实参**。

```js
function fun1() {
    console.log(arguments); //输出一个伪数组
    console.log(arguments.length); //输出3
}
fun1(1,2,3);
```

arguments展示形式是一个**伪数组**，因此可以进行遍历。伪数组具有以下特点：

- 具有 length 属性
- 按索引方式储存数据
- 不具有数组的 push , pop 等方法

> 注意只有函数才有 arguments 对象。

**求任意个数的最大值**：

```js
function maxValue() {
    var max = arguments[0];
    for (var i = 0; i < arguments.length; i++) {
        if (max < arguments[i]) {
            max = arguments[i];
        }
    }
    return max;
}
console.log(maxValue(2, 4, 5, 9));
console.log(maxValue(12, 4, 9));
```

### 六、函数案例

**翻转任意一个数组**：

```js
function reverse(arr) {
    var newArr = [];
    for (var i = arr.length - 1; i >= 0; i--) {
        newArr[newArr.length] = arr[i];
    }
    return newArr;
}
var arr1 = reverse([1, 3, 4, 6, 9]);
console.log(arr1);
```

**冒泡排序**：

```js
function sort(arr) {
    for (var i = 0; i < arr.length - 1; i++) {
        for (var j = 0; j < arr.length - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                var temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    return arr;
}
```

**判断闰年**：

```js
function isRun(year) {
    var flag = false;
    if (year % 4 === 0 && year % 100 !== 0 || year % 400 === 0) {
        flag = true;
    }
    return flag;
}
console.log(isRun(2010));
console.log(isRun(2012));
```

**函数的相互调用**：

```js
function fn1() {
    console.log(111);
    fn2();
    console.log('fn1');
}
function fn2() {
    console.log(222);
    console.log('fn2');
}
fn1(); //111，222，fn2，fn1
```

### 七、函数的两种声明方式

#### 1. 自定义函数方式(命名函数)

利用函数关键字 function 自定义函数方式。

- 因为有名字，所以也被称为**命名函数**
- 调用函数的代码既可以放到声明函数的**前面**，也可以放在声明函数的**后面**

#### 2. 函数表达式方式(匿名函数）

利用函数表达式方式的写法如下：

```js
// 这是函数表达式写法，匿名函数后面跟分号结束
var fn = function(){...}；
// 调用的方式，函数调用必须写到函数体下面
fn();
```

- 因为函数**没有名字**，所以也被称为**匿名函数**
- 这个 fn 里面存储的是一个函数
- 函数表达式方式原理跟声明变量方式是一致的
- 函数调用的代码必须写到**函数体后**

## 九、JavaScript作用域

### 一、作用域

通常来说，一段程序代码中所用到的名字并不总是有效和可用的，而限定这个名字的可用性的代码范围就是这个名字的**作用域**。作用域的使用提高了程序逻辑的局部性，增强了程序的可靠性，减少了名字冲突。

```js
var num =10;
console.log(num); //10 全局作用域
function fn() {
    var num=20;
    console.log(num); //20 局部作用域
}
fn();
```

### 二、变量的作用域

在JavaScript中，根据作用域的不同，变量可以分为两种：**全局变量**、**局部变量**

#### 1. 全局变量

```js
var num =10; //全局变量
console.log(num); 
function fn() {
    console.log(num); //可以访问
    num1 =10； //也是全局变量
}
fn();
```

> 在全局作用域下声明的变量叫做全局变量（在函数外部定义的变量）。

- 全局变量在代码的任何位置都可以使用
- 在全局作用域下var声明的变量是全局变量
- 特殊情况下，在函数内不使用var声明的变量也是全局变量（不建议使用）

#### 2. 局部变量

```js
function fn(arg) { //形参也是局部变量
    var num =10; //局部变量
    console.log(num); //可以访问
}
fn();
```

> 在局部作用域下声明的变量叫做局部变量（在函数内部定义的变量）

- 局部变量只能在该函数**内部**使用
- 在函数内部var声明的变量是局部变量
- 函数的**形参**实际上就是局部变量

#### 3. 全局变量和局部变量的区别

- 全局变量：在任何一个地方都可以使用，只有在浏览器关闭时才会被销毁，因此比较占内存
- 局部变量：只在函数内部使用，当其所在的代码块被执行时，会被初始化；当代码块运行结束后，就会被销毁，因此更节省内存空间

> 注意：ES5没有块级作用域。因此以下代码可以正常执行。

```js
if (3 < 5) { // 块级
    var num = 1;
}
console.log(num);
```

### 三、作用域链

- 只要是代码，就至少有一个作用域
- 写在函数内部的**局部**作用域
- 如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域
- 根据在内部函数可以访问外部函数变量的这种机制，用**链式查找**决定哪些数据能被内部函数访问，就称作作用域链

```js
var num=10;
function fn1() { //外部函数
    function fn2() { // 内部函数
        console.log(num); // 就近原则访问 20
    }
    var num=20;
    fn2();
}
fn1();
```

## 十、JavaScript预解析

### 预解析

JavaScript代码是由浏览器中的JavaScript解析器来执行的。JavaScript解析器在运行JavaScript代码的时候分为两步：**预解析**和**代码执行**。

- 预解析**js**引擎会把js里面所有的var还有function提升到当前作用域的最前面
- 代码执行按照代码书写的顺序从上往下执行

预解析分为变量预解析（变量提升）和函数预解析（函数提升）

- **变量提升** 就是把所有的变量声明提升到当前的作用域最前面，不提升赋值操作
- **函数提升** 就是把所有的函数声明提开到当前作用域的最前面，不调用函数

```js
console.log(num);
var num = 10; // undefined
//相当于执行了以下代码
var num;
console.log(num);
num = 10;
```

```js
fun();//报错坑2
var fun = function () {
    console.log(22);
}
//相当于执行了以下代码
var fun;
fun();
fun = function () {
    console.log(22);
}
```

> 总结：函数表达式调用必须写在函数表达式的下面。

**案例1**：

```js
//案例1
var num = 10;
fun();
function fun() {
    console.log(num);
    var num = 20;
}
```

> 结果是undefined，因为先找fun里的num，由于在下面，再根据变量提升，可以得到答案。

```js
//相当于以下操作：
var num;
function fun() {
    var num;
    console.log(num);
    num = 20;
}
num = 10;
fun();
```

**案例2**：

```js
f1();
console.log(c);
console.log(b);
console.log(a);

function f1() {
    var a = b = c = 9; //相当于 var a=9;b=9;c=9;
    console.log(a);
    console.log(b);
    console.log(c);
}
```

> 结果是9，9，9，9，9，报错。注意b和c是全局变量，a是局部变量。

## 十一、JavaScript 对象

### 一、对象

#### 1. 什么是对象

对象是一个**具体的事物**，看得见摸得着的实物。

在 JavaScript 中，对象是一组无序的相关属性和方法的集合，所有的事物都是对象，例如字符串、数值、数组、 函数等。

对象是由**属性**和**方法**组成的。

**属性**：事物的特征，在对象中用属性来表示（常用名词）

**方法**：事物的行为，在对象中用方法来表示（常用动词）

#### 2. 为什么需要对象

JS 中的对象表达结构更清晰，更强大，可以保存更加完整的信息。

### 二、创建对象的三种方式

在 JavaScript 中，现阶段我们可以采用三种方式创建对象（object）：

- 利用字面量创建对象
- 利用 new Object 创建对象
- 利用构造函数创建对象

#### 1. 利用字面量创建对象

对象字面量：就是花括号 { } 里面包含了表达这个具体事物（对象）的属性和方法。

{ } 里面采取**键值对**的形式表示

键：相当于属性名

值：相当于属性值，可以是任意类型的值（数字类型、字符串类型、布尔类型，函数类型等）

```js
var star = {
    name : 'pink', 
    age : 18,
    sex : '男',
    sayHi : function(){
        alert('大家好啊~');
    }
};
```

> 注意键值对要用**逗号**隔开。

**对象的调用**：

对象里面的属性调用 : **对象.属性名** ，这个小点 . 就理解为“ 的 ”

对象里面属性的另一种调用方式 : **对象[‘属性名’]**，注意方括号里面的属性必须加引号，我们后面会用

对象里面的方法调用：**对象.方法名()** ，注意这个方法名字后面一定加括号

```js
console.log(star.name) // 调用名字属性
console.log(star['name']) // 调用名字属性
star.sayHi(); // 调用 sayHi 方法,注意，一定不要忘记带后面的括号
```

**变量、属性、函数、方法总结**：

**变量**：单独声明赋值，单独存在

**属性**：对象里面的变量称为属性，不需要声明，用来描述该对象的特征

**函数**：单独存在的，通过“函数名()”的方式就可以调用

**方法**：对象里面的函数称为方法，方法不需要声明，使用“对象.方法名()”的方式就可以调用，方法用来描述该对象的行为和功能。

#### 2. 利用new Object创建对象

```js
var andy = new Obect();
andy.name = 'pink';
andy.age = 18;
andy.sex = '男';
andy.sayHi = function(){
    alert('大家好啊~');
}
```

> 我们是利用等号**=**赋值的方法添加对象的属性和方法。每个属性和方法之间用**分号**结束

Object() ：第一个字母**大写**

new Object() ：需要 new 关键字

使用的格式：对象.属性 = 值; 

#### 3. 利用构造函数创建对象

**构造函数**：是一种特殊的函数，主要用来初始化对象，即为对象成员变量赋初始值，它总与 **new** 运算符一起 使用。我们可以把对象中一些公共的属性和方法抽取出来，然后封装到这个函数里面。

在 js 中，使用构造函数要时要注意以下两点：

- 构造函数用于创建某一类对象，其首字母要大写
- 构造函数要和 **new** 一起使用才有意义

```js
function Person(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
    this.sayHi = function() {
        alert('我的名字叫：' + this.name + '，年龄：' + this.age + '，性别：' + this.sex);
    }
}
var bigbai = new Person('大白', 100, '男');
var smallbai = new Person('小白', 21, '男');
console.log(bigbai.name);
console.log(smallbai.name);
```

**注意**：

- 构造函数约定**首字母大写**。是**规范**而已。
- 函数内的属性和方法前面需要添加 **this** ，表示当前对象的属性和方法。
- 构造函数中**不**需要 **return** 返回结果。
- 当我们创建对象的时候，必须用 **new** 来调用构造函数。

#### 4. 构造函数和对象

**构造函数**：泛指的某一大类，它类似于 java 语言里面的类（class）

**对象**：特指是一个具体的事物

> 我们利用构造函数创建对象的过程我们也称为对象的**实例化**。

### 三、new关键字

new 在执行时会做四件事情：

1. 在内存中创建一个新的空对象。
2. 让 this 指向这个新的对象。
3. 执行构造函数里面的代码，给这个新对象添加属性和方法。
4. 返回这个新对象（所以构造函数里面不需要return）。

### 四、遍历对象属性

for...in 语句用于对数组或者对象的属性进行循环操作。

其语法如下：

```js
for (变量 in 对象名字) {
    // 在此执行代码
}
```

```js
for (var k in obj) {
    console.log(k); // 这里的 k 是属性名
    console.log(obj[k]); // 这里的 obj[k] 是属性值
}
```

> 语法中的变量是自定义的，它需要符合命名规范，通常我们会将这个变量写为 k 或者 key。

### 五、小结

1. 对象可以让代码结构更清晰
2. 对象复杂数据类型object。
3. 本质：对象就是一组无序的相关属性和方法的集合。
4. 构造函数泛指某一大类，比如苹果，不管是红色苹果还是绿色苹果，都统称为苹果。
5. 对象实例特指一个事物，比如这个苹果、正在给你们讲课的pink老师等。
6. for...in 语句用于对对象的属性进行循环操作。

## 十二、JavaScript 内置对象

### 一、内置对象

JavaScript 中的对象分为3种：**自定义对象** 、**内置对象**、 **浏览器对象**

前面两种对象是JS 基础 内容，属于 ECMAScript； 第三个浏览器对象属于我们JS 独有的， JS API 讲解

**内置对象**就是指 JS 语言**自带**的一些对象，这些对象供开发者使用，并提供了一些常用的或是最基本而必要的功能（属性和方法）

内置对象最大的优点就是帮助我们**快速开发**

JavaScript 提供了多个内置对象：Math、 Date 、Array、String等

### 二、查文档

#### MDN

Mozilla 开发者网络（MDN）提供了有关开放网络技术（Open Web）的信息，包括 HTML、CSS 和万维网及 HTML5 应用的 API。

MDN: https://developer.mozilla.org/zh-CN/

1. 查阅该方法的功能
2. 查看里面参数的意义和类型
3. 查看返回值的意义和类型
4. 通过 demo 进行测试

### 三、Math对象

#### 1. 概述

Math 对象**不是**构造函数，它具有数学常数和函数的属性和方法。跟数学相关的运算（求绝对值，取整、最大值 等）可以使用 Math 中的成员。

```js
Math.PI // 圆周率
Math.floor() // 向下取整
Math.ceil() // 向上取整
Math.round() // 四舍五入版 就近取整 注意 -3.5 结果是 -3 
Math.abs() // 绝对值
Math.max()/Math.min() // 求最大和最小值
```

> 注意：上面的方法必须带括号

```js
Math.abs('-1') // -1 隐式转换
Math.abs('pink') //NaN

Math.round(-1.5) //-1  .5特殊，往大了取
```

#### 2. 随机数方法 random

random() 方法可以随机返回一个小数，其取值范围是 [0，1)，左闭右开 0 <= x < 1。

**得到一个两数之间的随机整数包括两个数在内**：

```js
function getRandom(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
```

### 三、日期对象

#### 1. 概述

Date 对象和 Math 对象不一样，他是一个**构造函数**，所以我们需要实例化后才能使用。

 Date 实例用来处理日期和时间。

#### 2. Date()方法的使用

**获取当前时间必须实例化**：

```js
var now = new Date();
console.log(now);
```

**Date() 构造函数的参数**:

如果括号里面有时间，就返回参数里面的时间。例如日期格式字符串为‘2019-5-1’，可以写成new Date('2019-5-1') 或 者 new Date('2019/5/1')

- 如果Date()不写参数，就返回当前时间
- 如果Date()里面写参数，就返回括号里面输入的时间

#### 3. 日期格式化

需要获取日期指定的部分，所以我们要手动的得到这种格式。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/afb7eda6d92f77ce2de28dd8a03a96b4.jpg" alt="afb7eda6d92f77ce2de28dd8a03a96b4.jpg" border="0" />

**输出当前日期**：

```js
var date=new Date();
var year=date.getFullYear();
var month=date.getMonth() + 1;
var dates=date.getDate();
var arr=['星期日','星期一','星期二','星期三','星期四','星期五','星期六'];
var day=arr[date.getDay()];
console.log('今天是：'+year+'年'+month+'月'+dates+'日  '+day);
```

**输出当前日期时间**：

```js
function getTime() {
    var time = new Date();
    var h = time.getHours();
    h = h < 10 ? '0' + h : h;
    var m = time.getMinutes();
    m = m < 10 ? '0' + m : m;
    var s = time.getSeconds();
    s = s < 10 ? '0' + s : s;
    return h + ':' + m + ':' + s;
}
console.log(getTime());
```

#### 4. 日期总的毫秒形式

Date 对象是基于1970年1月1日（世界标准时间）起的毫秒数。**时间戳**。

```js
// 实例化Date对象
var now = new Date();
// 1. 用于获取对象的原始值
console.log(now.valueOf())
console.log(now.getTime())
// 2. 简单写可以这么做
var now1 = + new Date();
console.log(now1);
// 3. HTML5中提供的方法，有兼容性问题
var now2 = Date.now();
console.log(now2);
```

**倒计时效果**：

```js
function countDown(time) {
    var nowTime = +new Date(); //返回当前时间的总毫秒数
    var inputTime = +new Date(time); // 返回用户输入时间的总毫秒数
    var times = (inputTime - nowTime) / 1000; // 剩余时间的总秒数
    var d = parseInt(times / 60 / 60 / 24); // 计算天数
    d = d < 10 ? '0' + d : d;
    var h = parseInt(times / 60 / 60 % 24) // 计算小时
    h = h < 10 ? '0' + h : h;
    var m = parseInt(times / 60 % 60); // 计算分数
    m = m < 10 ? '0' + m : m;
    var s = parseInt(times % 60); // 计算当前秒数
    s = s < 10 ? '0' + s : s;
    return d+'天'+h+'时'+m+'分'+s+'秒';
}
console.log(countDown('2021-6-23 18:00:00'));
```

### 四、数组对象

#### 1. 数组对象的创建

```js
var arr=new Array(2,3);// 等价于[2，3]
var arr=new Array(2);// 这个2表示数组长度是2
var arr1=new Array();// 空数组
```

#### 2. 检测是否为数组

**instanceof** 运算符，可以判断一个对象是否属于某种类型。

Array.isArray()用于判断一个对象是否为数组，**isArray()** 是 HTML5 中提供的方法。

```js
var arr = [1, 23];
var obj = {};
console.log(arr instanceof Array); // true
console.log(obj instanceof Array); // false
console.log(Array.isArray(arr)); // true
console.log(Array.isArray(obj)); // false
```

#### 3. 添加删除数组元素的方法

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/ba3985184f40bb0726aac26164b9a891.jpg" alt="ba3985184f40bb0726aac26164b9a891.jpg" border="0" />

#### 4. 数组排序

```js
var arr = [1, 23, 7, 2];
arr.reverse(); //翻转
arr.sort(function (a,b) {
    return a-b;//升序
    return b-a;//降序
}); 
```

#### 5. 数组索引方法

```js
var arr=['blue','red','yellow'];
console.log(arr.indexOf('blue'));// 返回满足条件的第一个索引号
//没找到就返回-1
console.log(arr.lastIndexOf('blue'));// 从后面开始查找的第一个
```

**数组去重**：

```js
function unique(arr) {
    var newArr = [];
    for (var i = 0; i < arr.length; i++) {
        if (newArr.indexOf(arr[i]) === -1) {
            newArr.push(arr[i]);
        }
    }
    return newArr;
}
```

#### 6. 数组转换为字符串

```js
var arr=[1,2,3];
console.log(arr.toString()); //转字符串
var arr=['1','ss','pink'];
console.log(arr.join('-'));// 自定义分隔符
```

### 五、字符串对象

#### 1. 基本包装类型

为了方便操作基本数据类型，JavaScript 还提供了三个特殊的引用类型：**String**、**Number**和 **Boolean**。 

**基本包装类型**就是把简单数据类型**包装**成为复杂数据类型，这样基本数据类型就有了属性和方法。

```js
// 下面代码有什么问题？
var str = 'andy';
console.log(str.length);
```

基本数据类型是没有属性和方法的，而对象才有属性和方法，但上面代码却可以执行，这是因为 js 会把 基本数据类型包装为复杂数据类型，其执行过程如下：

```js
// 1. 生成临时变量，把简单类型包装为复杂数据类型
var temp = new String('andy');
// 2. 赋值给我们声明的字符变量
str = temp;
// 3. 销毁临时变量
temp = null;
```

#### 2. 字符串的不可变

指的是里面的值不可变，虽然看上去可以改变内容，但其实是**地址**变了，内存中新开辟了一个内存空间。

```js
var str = 'abc';
str = 'hello';
// 当重新给 str 赋值的时候，常量'abc'不会被修改，依然在内存中
// 重新给字符串赋值，会重新在内存中开辟空间，这个特点就是字符串的不可变
// 由于字符串的不可变，在大量拼接字符串的时候会有效率问题
var str = '';
for (var i = 0; i < 100000; i++) {
    str += i;
}
console.log(str); // 这个结果需要花费大量时间来显示，因为需要不断的开辟新的空间
```

#### 3. 根据字符返回位置

```js
var str = '改革春风吹满地，春天来了！';
console.log(str.indexOf('春'));
console.log(str.indexOf('春',3)); // 从索引号是3的位置开始查找
```

**返回字符位置**：

```js
var str="jihjihhokhk";
var index=str.indexOf('o');
while(index!==-1){
    console.log(index);
    index=str.indexOf('o',index+1);
}
```

#### 4. 根据位置返回字符

```js
var str='andy';
console.log(str.charAt(3));// 根据位置返回字符
console.log(str.charCodeAt(0)); // 返回相应索引号的字符ASCII值
console.log(str[0]); // 获取指定位置字符
```

**返回出现次数最多的字符**：

```js
var str = 'sdfogosogs';
var o = {};
for (var i = 0; i < str.length; i++) {
    var chars = str.charAt(i);
    if (o[chars]) { // 判断对象是否有该属性
        o[chars]++;
    } else {
        o[chars] = 1;
    }
}
var max = 0, ch = '';
for (var k in o) { // 遍历对象
    if (o[k] > max) {
        max = o[k];
        ch = k;
    }
}
console.log(max,ch);
```

#### 5. 字符串操作方法

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/f7b75a23a974a05fbd28582d2e9fc74d.jpg" alt="f7b75a23a974a05fbd28582d2e9fc74d.jpg" border="0" />

#### 6. replace()方法

replace() 方法用于在字符串中用一些字符替换另一些字符。

```js
var str='adcd';
console.log(str.replace('d','b')); //替换第一个
```

#### 7. split()方法

split()方法用于切分字符串，它可以将字符串切分为**数组**。在切分完毕之后，返回的是一个**新数组**。

```js
var str='red,green,yellow';
console.log(str.split(',')); // 按逗号分割，返回数组
```

## 十三、JavaScript 简单类型与复杂类型

### 一、简单类型与复杂类型

简单类型又叫做基本数据类型或者**值类型**，复杂类型又叫做**引用类型**。

**值类型**：简单数据类型/基本数据类型，在存储时变量中存储的是值本身，因此叫做值类型

string ，number，boolean，undefined，null

**引用类型**：复杂数据类型，在存储时变量中存储的仅仅是地址（引用），因此叫做引用数据类型

通过 **new** 关键字创建的对象（系统对象、自定义对象），如 Object、Array、Date等

### 二、堆和栈

**栈**（操作系统）：由操作系统自动分配释放存放函数的参数值、局部变量的值等。其操作方式类似于数据结构中的栈； 简单数据类型存放到栈里面 

**堆**（操作系统）：存储复杂类型(对象)，一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收。 复杂数据类型存放到堆里面

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/5dd168fe9656e6c95746e2d63de3d632.jpg" alt="5dd168fe9656e6c95746e2d63de3d632.jpg" border="0" />

> 注意：JavaScript中没有堆栈的概念，通过堆栈的方式，可以让大家更容易理解代码的一些执行方式，便于将来学习其他语言。

### 三、简单类型的内存分配

**值类型**（简单数据类型）： string ，number，boolean，undefined，null

值类型变量的数据直接存放在变量（**栈空间**）中

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/bfbe2c343b460aeba3db485326d7b3b6.jpg" alt="bfbe2c343b460aeba3db485326d7b3b6.jpg" border="0" />

### 四、复杂类型的内存分配

**引用类型**（复杂数据类型）：通过 new 关键字创建的对象（系统对象、自定义对象），如 Object、Array、Date等

引用类型变量（栈空间）里存放的是**地址**，真正的对象实例存放在**堆空间**中

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/4ad7f37f2fd922169dba221bc1c2c060.jpg" alt="4ad7f37f2fd922169dba221bc1c2c060.jpg" border="0" />

### 五、简单类型传参

```js
function fn(a) {
    a++;
    console.log(a); //11
}
var x = 10;
fn(x);
console.log(x); //10
```

函数的形参也可以看做是一个变量，当我们把一个值类型变量作为参数传给函数的形参时，其实是把变量在栈空间里的值**复制**了一份给形参，那么在方法内部对形参做任何修改，都**不会影响**到的外部变量。

#### 复杂类型传参

```js
function Person(name) {
    this.name = name;
}
function f1(x) { // x = p，地址赋值
    console.log(x.name); // 2. 刘德华
    x.name = "张学友";
    console.log(x.name); // 3. 张学友
}
var p = new Person("刘德华");
console.log(p.name); // 1. 刘德华
f1(p);
console.log(p.name); // 4. 张学友
```

函数的形参也可以看做是一个变量，当我们把引用类型变量传给形参时，其实是把变量在栈空间里保存的堆地址复制给了形参，形参和实参其实保存的是**同一个堆地址**，所以操作的是**同一个对象**。

## 十四、Web APIs简介

### 一、Web APIs和JS基础关联性

#### 1. JS的组成

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/e9818ac75a3e4b33c12af82a90e7daec.jpg" alt="e9818ac75a3e4b33c12af82a90e7daec.jpg" border="0" />

#### 2. JS基础阶段以及Web APIs阶段

**JS基础阶段**：

- 我们学习的是ECMAScript标准规定的基本语法
- 只学习基本语法，做不了常用的网页交互效果
- 目的是为了JS后面的课程打基础、做铺垫

**Web APIs阶段**：

- Web APIs是W3C组织的标准
- Web APIs我们主要学习DOM和BOM
- Web APIs是我们JS所独有的部分
- 主要学习页面交互功能

### 二、API和Web API

#### 1. API

API（Application Programming Interface，应用程序编程接口）是一些预先定义的**函数**，目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力，而又无需访问源码，或理解内部工作机制的细节。

> 简单理解：API是给程序员提供的一种工具，以便能更轻松的实现想要完成的功能。

#### 2. Web API

Web API是浏览器提供的一套操作**浏览器功能**和**页面元素**的**API**（BOM和DOM）。

现阶段我们主要针对于浏览器讲解常用的API，主要针对浏览器做交互效果。

MDN详细API：https://developer.mozilla.org/zh-CN/docs/Web/API

#### 3. 总结

**API**是为我们程序员提供的一个接口，帮助我们实现某种功能，我们会使用就可以了，不必纠结内部如何实现

**Web API**主要是针对于浏览器提供的接口，主要针对于浏览器做交互效果。

**Web API**一般都有输入和输出（函数的传参和返回值），Web API很多都是方法（函数）

## 十五、DOM

### 一、DOM 简介

#### 1. 什么是DOM

**文档对象模型**（Document Object Model，简称 **DOM**），是 W3C 组织推荐的处理可扩展标记语言（HTML 或者XML）的标准**编程接口**。

W3C 已经定义了一系列的 DOM 接口，通过这些 DOM 接口可以改变网页的内容、结构和样式。

#### 2. DOM 树

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/497553f788235b914667388eacfcf622.jpg" alt="497553f788235b914667388eacfcf622.jpg" border="0" />

**文档**：一个页面就是一个文档，DOM 中使用 **document** 表示

**元素**：页面中的所有标签都是元素，DOM 中使用 **element** 表示

**节点**：网页中的所有内容都是节点（标签、属性、文本、注释等），DOM 中使用 **node** 表示 

> DOM 把以上内容都看做是对象

### 二、获取元素

#### 1. 如何获取页面元素

获取页面中的元素可以使用以下几种方式：

- 根据 ID 获取
- 根据标签名获取
- 通过 HTML5 新增的方法获取
- 特殊元素获

#### 2. 根据 ID 获取

使用 **getElementById**() 方法可以获取带有 ID 的元素对象。

```html
<div id="time">2021-5-5</div>
<script>
    var times=document.getElementById('time');
    console.dir(times); //推荐使用
</script>
```

- 因为我们文档页面从上往下加载，所以先得有标签，所以我们script写到标签的下面
- 参数id是大小写敏感的字符串
- 返回的是一个元素对象

#### 3. 根据标签名获取

使用 **getElementsByTagName**() 方法可以返回带有指定标签名的对象的集合。

```html
<ul>
    <li>1</li>
    <li>1</li>
    <li>1</li>
    <li>1</li>
    <li>1</li>
</ul>
<script>
    //返回的是获取过来元素对象的集合以伪数组的形式存储的
    var lis = document.getElementsByTagName('li');
    console.dir(lis);
    //遍历得到所有的元素
    for (var i = 0; i < lis.length; i++) {
        console.log(lis[i]);
    }
    //如果页面中只有一个li返回的还是伪数组的形式，没有元素返回的空的伪数组的形式
</script>
```

**若要获取某个父元素下的子元素**：

```js
var ol=document.getElementsByTagName('ol');
console.log(ol[0].getElementsByTagName('li'));
//或者给ol指定id可以这么写
console.log(ol.getElementsByTagName('li'));
```

> 注意：父元素必须是单个对象（必须指明是哪一个元素对象）。获取的时候不包括父元素自己。

#### 4. 通过 HTML5 新增的方法获取

```js
//根据类名返回元素对象集合
var boxs=document.getElementsByClassName('box');
console.log(boxs);
```

```js
// 根据指定选择器返回第一个元素对象
var firstBox=document.querySelector('.box');
var nav=document.querySelector('#nav');
var nav=document.querySelector('li');
```

```js
// 根据指定选择器返回，得到所有
var allBox=document.querySelectorAll('.box');
```

> 注意： querySelector 和 querySelectorAll里面的选择器需要加符号,比如:document.querySelector('#nav');

#### 5. 获取特殊元素（body，html）

**获取body元素**：

```js
var body = document.body // 返回body元素对象
```

**获取html元素**：

```js
var html = document.documentElement // 返回html元素对象
```

### 三、事件基础

#### 1. 概述

JavaScript 使我们有能力创建动态页面，而**事件**是可以被 JavaScript 侦测到的行为。

简单理解： **触发**--- **响应机制**。

网页中的每个元素都可以产生某些可以触发 JavaScript 的事件，例如，我们可以在用户点击某按钮时产生一个**事件**，然后去执行某些操作。

#### 2. 事件三要素

1. 事件源 （谁）
2. 事件类型 （什么事件）
3. 事件处理程序 （做啥）

**点击按钮弹出警示框**：

```js
var btn = document.getElementById('btn');
btn.onclick = function() {
    alert('你好吗');
};
```

#### 3. 执行事件的步骤

1. 获取事件源
2. 注册事件（绑定事件）
3. 添加事件处理程序（采取函数赋值形式）

**常见的鼠标事件**：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/19/a5881cba19a722efa079fe849a53a1b2.jpg" alt="a5881cba19a722efa079fe849a53a1b2.jpg" border="0" />

### 四、操作元素

JavaScript 的 DOM 操作可以改变网页内容、结构和样式，我们可以利用 DOM 操作元素来改变元素里面的内容 、属性等。注意以下都是属性。

#### 1. 改变元素内容

```js
var btn = document.querySelector('button');
var div = document.querySelector('div');
btn.onclick = function () {
    div.innerText='2021-6-19'; // 修改内容
}
```

> 从起始位置到终止位置的内容, 但它去除 html 标签，同时空格和换行也会去掉。

```js
var div = document.querySelector('div');
div.innerHTML = '<strong>2021-6-19</strong>'; // 支持识别html标签 推荐
```

> 起始位置到终止位置的全部内容，包括 html 标签，同时保留空格和换行。**推荐**

#### 2. 常用元素的属性操作

1. innerText、innerHTML 改变元素内容
2. src、href
3. id、alt、title

```js
//修改元素属性 src
//获取元素
var ldh=document.getElementById('ldh');
var zxy=document.getElementById('zxy');
var img=document.querySelector('img');
//注册事件
zxy.onclick=function () {
    img.src='zxy.jpg';
    img.title='zxy';
}
ldh.onclick=function () {
    img.src='ldh.jpg';
    img.title='ldh';
}
```

#### 3. 表单元素的属性操作

利用 DOM 可以操作如下表单元素的属性：

type、value、checked、selected、disabled

如：

```js
var btn=document.querySelector('button');
var input=document.querySelector('input');
btn.onclick=function () {
    input.value='被点击了'; // 表单里的值是通过value修改的
    this.disabled=true; // 禁用按钮
    //this 指向函数的调用者
}
```

**仿京东显示密码**：

```js
var eye=document.getElementById('eye');
var pwd=document.getElementById('pwd');
var flag=1;
eye.onclick=function () {
    if(!flag){
        pwd.type='text';
        eye.src='xx.png';
    }else{
        pwd.type='password';
        eye.src='xxx.png';
        flag=0;
    }
}
```

#### 4. 样式属性操作

我们可以通过 JS 修改元素的大小、颜色、位置等样式。

```js
var div=document.querySelector('div');
div.onclick=function () {
    this.style.backgroundColor='pink';
    this.style.width='250px';
}
```

> 注意：JS 里面的样式采取**驼峰命名法** 比如fontSize、 backgroundColor；JS 修改 style 样式操作，产生的是**行内样式**，CSS 权重比较**高**

**淘宝点击关闭二维码**：

```js
var btn=document.querySelector('.close-btn');
var box=document.querySelector('.box');
btn.onclick =function () {
    box.style.display='none';
}
```

**循环精灵图背景**：

```js
var lis = document.querySelectorAll('li');
for (var i = 0; i < lis.length; i++) {
    //让索引号乘44就是背景y坐标，找规律得到
    var index = i * 44;
    lis[i].style.backgroundPosition = '0 -' + index + 'px';
}
```

**显示隐藏文本框内容**：

```js
// 1.获取元素
var text = document.querySelector('input');
// 2.注册事件 获得焦点事件 onfocus 
text.onfocus = function() {
    // console.log('得到了焦点');
    if (this.value === '手机') {
        this.value = '';
    }
    // 获得焦点需要把文本框里面的文字颜色变黑
    this.style.color = '#333';
}
// 3. 注册事件 失去焦点事件 onblur
text.onblur = function() {
    // console.log('失去了焦点');
    if (this.value === '') {
        this.value = '手机';
    }
    // 失去焦点需要把文本框里面的文字颜色变浅色
    this.style.color = '#999';
}
```

**类名样式操作**：

```js
var test = document.querySelector('div');
test.onclick = function() {
    this.className = 'change';
}
```

> 注意：
>
> - 如果样式修改较多，可以采取操作类名方式更改元素样式。
> - class因为是个保留字，因此使用className来操作元素类名属性
> - className 会直接更改元素的类名，会覆盖原先的类名。

#### 5. 排他思想

如果有**同一组**元素，我们想要某一个元素实现某种样式，需要用到循环的**排他思想**算法。

1. 所有元素全部清除样式
2. 给当前元素设置样式 
3. 注意顺序不能颠倒，首先干掉其他人，再设置自己

```js
// 1. 获取所有按钮元素
var btns = document.getElementsByTagName('button');
// btns得到的是伪数组  里面的每一个元素 btns[i]
for (var i = 0; i < btns.length; i++) {
    btns[i].onclick = function() {
        // (1) 我们先把所有的按钮背景颜色去掉  干掉所有人
        for (var i = 0; i < btns.length; i++) {
            btns[i].style.backgroundColor = '';
        }
        // (2) 然后才让当前的元素背景颜色为pink 留下我自己
        this.style.backgroundColor = 'pink';

    }
}
```

**百度换肤**：

```js
// 1. 获取元素 
var imgs = document.querySelector('.baidu').querySelectorAll('img');
// 2. 循环注册事件 
for (var i = 0; i < imgs.length; i++) {
    imgs[i].onclick = function() {
        // this.src 就是我们点击图片的路径 
        document.body.style.backgroundImage = 'url(' + this.src + ')';
    }
}
```

**表格隔行变色**：

```js
// 1.获取元素 获取的是 tbody 里面所有的行
var trs = document.querySelector('tbody').querySelectorAll('tr');
// 2. 利用循环绑定注册事件
for (var i = 0; i < trs.length; i++) {
    // 3. 鼠标经过事件 onmouseover
    trs[i].onmouseover = function() {
        this.className = 'bg';
    }
    // 4. 鼠标离开事件 onmouseout
    trs[i].onmouseout = function() {
        this.className = '';
    }
}
```

**表单全选取消全选**：

```js
// 1. 全选和取消全选做法：  让下面所有复选框的checked属性（选中状态） 跟随 全选按钮即可
// 获取元素
var j_cbAll = document.getElementById('j_cbAll'); // 全选按钮
var j_tbs = document.getElementById('j_tb').getElementsByTagName('input'); // 下面所有的复选框
// 注册事件
j_cbAll.onclick = function() {
    // this.checked 它可以得到当前复选框的选中状态如果是true 就是选中，如果是false 就是未选中
    console.log(this.checked);
    for (var i = 0; i < j_tbs.length; i++) {
        j_tbs[i].checked = this.checked;
    }
}
// 2. 下面复选框需要全部选中， 上面全选才能选中做法： 给下面所有复选框绑定点击事件，每次点击，都要循环查看下面所有的复选框是否有没选中的，如果有一个没选中的， 上面全选就不选中。
for (var i = 0; i < j_tbs.length; i++) {
    j_tbs[i].onclick = function() {
        // flag 控制全选按钮是否选中
        var flag = true;
        // 每次点击下面的复选框都要循环检查者4个小按钮是否全被选中
        for (var i = 0; i < j_tbs.length; i++) {
            if (!j_tbs[i].checked) {
                flag = false;
                break; // 退出for循环 这样可以提高执行效率 因为只要有一个没有选中，剩下的就无需循环判断了
            }
        }
        j_cbAll.checked = flag;
    }
}
```

#### 6. 自定义属性的操作

**获取属性值**：

```js
element.属性 获取属性值。
element.getAttribute('属性');
```

**区别**：

element.属性：获取**内置属性值**（元素本身自带的属性）

element.getAttribute('属性')：主要获得自定义的属性 （标准），程序员**自定义**

**设置属性值**：

```js
element.属性 = '值' 设置内置属性值。
element.setAttribute('属性', '值');
```

**区别**：

element.属性：设置**内置属性值**

element.setAttribute(‘属性’)：主要设置**自定义**的属性（标准）

**移除属性**：

```js
element.removeAttribute('属性');
```

> 注意：是直接删除整个属性，不是置空。

**tab 栏切换**：

```js
// 获取元素
var tab_list = document.querySelector('.tab_list');
var lis = tab_list.querySelectorAll('li');
var items = document.querySelectorAll('.item');
// for循环绑定点击事件
for (var i = 0; i < lis.length; i++) {
    // 开始给5个小li 设置索引号 
    lis[i].setAttribute('index', i);
    lis[i].onclick = function () {
        // 1. 上的模块选项卡，点击某一个，当前这一个底色会是红色，其余不变（排他思想） 修改类名的方式

        // 干掉所有人 其余的li清除 class 这个类
        for (var i = 0; i < lis.length; i++) {
            lis[i].className = '';
        }
        // 留下我自己 
        this.className = 'current';
        // 2. 下面的显示内容模块
        var index = this.getAttribute('index');
        console.log(index);
        // 干掉所有人 让其余的item 这些div 隐藏
        for (var i = 0; i < items.length; i++) {
            items[i].style.display = 'none';
        }
        // 留下我自己 让对应的item 显示出来
        items[index].style.display = 'block';
    }
}
```

#### 7. H5自定义属性

自定义属性目的：是为了保存并使用数据。有些数据可以**保存到页面**中而不用保存到数据库中。

但是有些自定义属性很容易**引起歧义**，不容易判断是元素的内置属性还是自定义属性。

H5给我们新增了自定义属性：

**设置H5自定义属性**：

H5规定自定义属性data-开头做为属性名并且赋值。

比如：

```html
<div data-index="1"></div>
```

或者使用 **JS 设置**：

```js
element.setAttribute('data-index', 2)
```

**获取H5自定义属性**：

**兼容性获取**：

```js
element.getAttribute('data-index');
```

**H5新增**：

```js
element.dataset.index
//或者
element.dataset['index']
```

> 注意：如果自定义属性里面有多个-链接的单词，我们获取的时候采取驼峰命名法；dataset是一个集合里面存放了所有以data开头的自定义属性

### 五、节点操作

#### 1. 为什么学节点操作

获取元素通常使用两种方式：

- 利用 DOM 提供的方法获取元素

> 逻辑性不强、繁琐

- 利用节点层级关系获取元素

> 逻辑性强， 但是兼容性稍差

#### 2. 节点概述

网页中的所有内容都是节点（标签、属性、文本、注释等），在DOM 中，节点使用 **node** 来表示。

HTML DOM 树中的所有节点均可通过 JavaScript 进行访问，所有 HTML 元素（节点）均可被**修改**，也可以创建或删除。

一般地，节点至少拥有**nodeType**（节点类型）、**nodeName**（节点名称）和**nodeValue**（节点值）这三个 基本属性。

- 元素节点 nodeType 为 1
- 属性节点 nodeType 为 2
- 文本节点 nodeType 为 3

> 我们在实际开发中，节点操作主要操作的是元素节点

#### 3. 节点层级

利用 DOM 树可以把节点划分为不同的层级关系，常见的是**父子兄层级关系**。

**父级节点**：

> **parentNode** 属性可返回某节点的父节点，注意是**最近**的一个父节点。如果指定的节点没有父节点则返回 **null**。

```js
var box=document.querySelector('.box');
console.log(box.parentNode);
```

**子节点**：

**parentNode.childNodes** 返回包含指定节点的子节点的集合，该集合为即时更新的集合。

```js
var uls=document.querySelector('ul');
console.log(uls.childNodes);
```

> 注意：返回值里面包含了所有的子节点，包括元素节点，文本节点等。 

> 如果只想要获得里面的元素节点，则需要专门处理。 所以我们**一般不提倡**使用childNode

<u>第二种方法：</u>

```js
var uls=document.querySelector('ul');
console.log(uls.children);
```

parentNode.children 是一个只读属性，返回所有的子元素节点。它只返回子**元素节点**，其余节点不返回（这个是我们重点掌握的）

<u>其它</u>：

```js
//firstElementChild 返回第一个子元素节点，找不到则返回null。
console.log(lis.firstElementChild);
//lastElementChild 返回最后一个子元素节点，找不到则返回null。 
console.log(lis.lastElementChild);
```

> 注意：这两个方法有兼容性问题，IE9 以上才支持。

<u>解决方案</u>：

如果想要第一个子元素节点，可以使用 

```js
parentNode.chilren[0]
```

如果想要最后一个子元素节点，可以使用

```js
parentNode.chilren[parentNode.chilren.length - 1]
```

**下拉菜单案例**：

```js
// 1. 获取元素
var nav = document.querySelector('.nav');
var lis = nav.children; // 得到4个小li
// 2.循环注册事件
for (var i = 0; i < lis.length; i++) {
    lis[i].onmouseover = function() {
        this.children[1].style.display = 'block';
    }
    lis[i].onmouseout = function() {
        this.children[1].style.display = 'none';
    }
}
```

**兄弟节点**：

```js
var div = document.querySelector('div');
// 1.nextSibling 下一个兄弟节点 包含元素节点或者 文本节点等等
console.log(div.nextSibling);
console.log(div.previousSibling);
// 2. nextElementSibling 得到下一个兄弟元素节点
console.log(div.nextElementSibling);
console.log(div.previousElementSibling);
//注意：这两个方法有兼容性问题， IE9 以上才支持
```

解决方法（自己封装一个函数）：

```js
function getNextElementSibling(element) {
    var el = element;
    while (el = el.nextSibling) {
        if (el.nodeType === 1) {
            return el;
        }
    }
    return null;
}
```

#### 4. 创建和添加节点

```js
// 1. 创建节点元素节点
var li = document.createElement('li');
// 2. 添加节点 node.appendChild(child)  node 父级  child 是子级 后面追加元素  类似于数组中的push
var ul = document.querySelector('ul');
ul.appendChild(li);
// 3. 添加节点 node.insertBefore(child, 指定元素);
var lili = document.createElement('li');
ul.insertBefore(lili, ul.children[0]);
// 4. 我们想要页面添加一个新的元素 ： 1. 创建元素 2. 添加元素
```

因为这些元素原先不存在， 是根据我们的需求动态生成的，所以我们也称为**动态创建元素节点**。

**简单版发布留言案例**：

```js
// 1. 获取元素
var btn = document.querySelector('button');
var text = document.querySelector('textarea');
var ul = document.querySelector('ul');
// 2. 注册事件
btn.onclick = function() {
    if (text.value == '') {
        alert('您没有输入内容');
        return false;
    } else {
        // (1) 创建元素
        var li = document.createElement('li');
        // 先有li 才能赋值
        li.innerHTML = text.value;
        // (2) 添加元素
        ul.insertBefore(li, ul.children[0]);
    }
}
```

#### 5. 删除节点

```js
// 1.获取元素
var ul = document.querySelector('ul');
// 2. 删除元素  node.removeChild(child)
ul.removeChild(ul.children[0]);
```

**删除留言案例**：

```js
var as = document.querySelectorAll('a');
for (var i = 0; i < as.length; i++) {
    as[i].onclick = function() {
        // node.removeChild(child); 删除的是 li 当前a所在的li  this.parentNode;
        ul.removeChild(this.parentNode);
    }
}
```

> 阻止链接跳转需要添加 javascript:void(0); 或者 javascript:

#### 6. 复制节点(克隆节点)

```js
node.cloneNode();
```

如果括号参数为空或者为 **false** ，则是**浅拷贝**，即只克隆复制节点本身，不克隆里面的子节点。如果括号参数为 **true** ，则是**深度拷贝**，会复制节点本身以及里面所有的子节点。

**动态生成表格案例**：

```js
// 1.先去准备好学生的数据
var datas = [{
    name: '魏璎珞',
    subject: 'JavaScript',
    score: 100
}];
// 2. 往tbody 里面创建行： 有几个人（通过数组的长度）我们就创建几行
var tbody = document.querySelector('tbody');
for (var i = 0; i < datas.length; i++) { // 外面的for循环管行 tr
    // 1. 创建 tr行
    var tr = document.createElement('tr');
    tbody.appendChild(tr);
    // 2. 行里面创建单元格(跟数据有关系的3个单元格) td 单元格的数量取决于每个对象里面的属性个数  for循环遍历对象 datas[i]
    for (var k in datas[i]) { // 里面的for循环管列 td
        // 创建单元格 
        var td = document.createElement('td');
        // 把对象里面的属性值 datas[i][k] 给 td
        td.innerHTML = datas[i][k];
        tr.appendChild(td);
    }
    // 3. 创建有删除2个字的单元格 
    var td = document.createElement('td');
    td.innerHTML = '<a href="javascript:;">删除 </a>';
    tr.appendChild(td);
}
// 4. 删除操作 开始 
var as = document.querySelectorAll('a');
for (var i = 0; i < as.length; i++) {
    as[i].onclick = function() {
        // 点击a 删除 当前a 所在的行(链接的爸爸的爸爸)  node.removeChild(child)  
        tbody.removeChild(this.parentNode.parentNode)
    }
}
```

#### 7. 三种动态创建元素区别

- document.write()

- element.innerHTML

- document.createElement()

**区别**：

1. document.write 是直接将内容写入页面的内容流，但是文档流执行完毕，则它会导致**页面全部重绘**
2. innerHTML 是将内容写入某个 DOM 节点，不会导致页面全部重绘
3. innerHTML 创建多个元素效率更高（不要拼接字符串，采取**数组形式拼接**），结构稍微复杂
4. createElement() 创建多个元素效率稍低一点点，但是结构更清晰

> 总结：不同浏览器下，innerHTML 效率要比 creatElement 

### 六、DOM 重点核心

<img src="https://img.zjgsuzjx.top/img/images/2021/06/20/eb018ca512dea8e5a1d2b7447d65dc09.jpg" alt="eb018ca512dea8e5a1d2b7447d65dc09.jpg" border="0" />

> 关于DOM操作，我们主要针对于元素的操作。主要有创建、增、删、改、查、属性操作、事件操作。

## 十六、事件高级

### 一、注册事件（绑定事件）

#### 1. 概述

给元素添加事件，称为注册事件或者绑定事件。注册事件有两种方式：**传统方式**和**方法监听注册方式**。

**传统注册方式**：注册事件的唯一性；同一个元素同一个事件只能设置一个处理函数，最后注册的处理函数将会**覆盖**前面注册的处理函数。

**方法监听注册方式**：w3c标准推荐方式；同一个元素同一个事件可以注册**多个**监听器；按注册**顺序**依次执行。

#### 2. addEventListener 事件监听方式

```js
var btns = document.querySelectorAll('button');
// 事件侦听注册事件 addEventListener 
// (1) 里面的事件类型是字符串 必定加引号 而且不带on
// (2) 同一个元素 同一个事件可以添加多个侦听器（事件处理程序）
btns[1].addEventListener('click', function () {
    alert(22);
})
btns[1].addEventListener('click', function () {
    alert(33);
})
```

该方法接收三个参数：

**type**：事件类型字符串，比如 **click** 、**mouseover** ，注意这里不要带 **on**

**listener**：事件处理函数，事件发生时，会调用该监听函数

**useCapture**：可选参数，是一个布尔值，默认是 false。

#### 3. attachEvent 事件监听方式

> 了解即可，早期版本用法。不用学。

### 二、删除事件（解绑事件）

#### 删除事件的方式

**传统注册方式**：

```js
var divs = document.querySelectorAll('div');
divs[0].onclick = function() {
    alert(11);
    // 1. 传统方式删除事件
    divs[0].onclick = null;
}
```

**方法监听注册方式**：

```js
// 2. removeEventListener 删除事件
var divs = document.querySelectorAll('div');
divs[1].addEventListener('click', fn) // 里面的fn 不需要调用加小括号
function fn() {
    alert(22);
    divs[1].removeEventListener('click', fn);
}
```

### 三、DOM事件流

**事件流**描述的是从页面中接收事件的顺序。 **事件**发生时会在元素节点之间按照特定的顺序传播，这个传播过程即 **DOM 事件流**。

DOM事件流分为3个阶段：

1. 捕获阶段（网景最早提出）
2. 当前目标阶段
3. 冒泡阶段（IE 最早提出）

<img src="https://img.zjgsuzjx.top/img/images/2021/06/20/6a5f1669d363379a477075ea2b10f6ef.jpg" alt="6a5f1669d363379a477075ea2b10f6ef.jpg" border="0" />

> 事件发生时会在元素节点之间按照特定的顺序传播，这个传播过程即 DOM 事件

```js
//第三个参数是 false 或者 省略 那么则处于冒泡阶段  son -> father ->body -> html -> document
var son = document.querySelector('.son');
son.addEventListener('click', function() {
    alert('son');
}, false);
var father = document.querySelector('.father');
father.addEventListener('click', function() {
    alert('father');
}, false);
document.addEventListener('click', function() {
    alert('document');
})
```

**注意**：

- JS 代码中只能执行捕获或者冒泡其中的**一个**阶段。

- **onclick** 和 **attachEvent** 只能得到**冒泡**阶段。

- addEventListener(type, listener[, useCapture])第三个参数如果是 **true**，表示在事件捕 获阶段调用事件处理程序；如果是 **false**（不写**默认**就是false），表示在事件冒泡阶段调用事件处理程序。

- 实际开发中我们很少使用事件捕获，我们**更**关注事件**冒泡**。

- 有些事件是**没有冒泡**的，比如 onblur、onfocus、onmouseenter、onmouseleave

### 四、事件对象

#### 1. 什么是事件对象

event 对象代表事件的状态，比如键盘按键的状态、鼠标的位置、鼠标按钮的状态。

> 跟事件相关的一系列信息数据的集合都放到这个对象里面，这个对象就是事件对象 **event**，它有很多属性和方法。

#### 2. 语法

```js
var div = document.querySelector('div');
div.onclick = function(e) { // 名字任意
    // e = e || window.event;
    console.log(e);
}
```

> 这个 **event** 是个形参，系统帮我们设定为事件对象，**不需要传递实参**过去。当我们注册事件时， **event** 对象就会被系统**自动创建**，并依次传递给事件监听器（事件处理函数）。

#### 3. 事件对象的常见属性和方法

<img src="https://img.zjgsuzjx.top/img/images/2021/06/20/fbc21658c3ead4e468759eb7c7778bf3.jpg" alt="fbc21658c3ead4e468759eb7c7778bf3.jpg" border="0" />

```js
// e.target 返回的是触发事件的对象（元素）  this 返回的是绑定事件的对象（元素）
var ul = document.querySelector('ul');
ul.addEventListener('click', function(e) {
    // 我们给ul 绑定了事件  那么this 就指向ul  
    console.log(this);
    console.log(e.currentTarget);
    // e.target 指向我们点击的那个对象 谁触发了这个事件 我们点击的是li e.target 指向的就是li
    console.log(e.target);
})
```

```js
// 阻止默认行为（事件） 让链接不跳转 或者让提交按钮不提交
var a = document.querySelector('a');
a.addEventListener('click', function(e) {
    e.preventDefault(); //  dom 标准写法
})
```

### 五、阻止事件冒泡

#### 阻止事件冒泡的两种方式

**事件冒泡**：开始时由最具体的元素接收，然后逐级向上传播到到 DOM 最顶层节。

```js
// 常见事件对象的属性和方法
// 阻止冒泡  dom 推荐的标准 stopPropagation()
var son = document.querySelector('.son');
son.addEventListener('click', function(e) {
    alert('son');
    e.stopPropagation(); // stop 停止  Propagation 传播
}, false);

var father = document.querySelector('.father');
father.addEventListener('click', function() {
    alert('father');
}, false);
document.addEventListener('click', function() {
    alert('document');
})
```

> 不阻止的话，点一个元素会引发其它元素的动作事件。

### 六、事件委托（代理、委派）

事件委托也称为事件代理， 在 jQuery 里面称为事件委派。

**原理**：

不是每个子节点单独设置事件监听器，而是事件监听器设置在其**父节点**上，然后利用**冒泡原理**影响设置**每个子节点**。 

**案例**：

给 **ul** 注册点击事件，然后利用事件对象的 **target** 来找到当前点击的 **li**，因为点击 **li**，事件会冒泡到 **ul** 上， **ul** 有注册事件，就会触发事件监听器。

**作用**：

我们只操作了一次 DOM ，提高了程序的性能。

```js
// 事件委托的核心原理：给父节点添加侦听器， 利用事件冒泡影响每一个子节点
var ul = document.querySelector('ul');
ul.addEventListener('click', function(e) {
    // alert('知否知否，点我应有弹框在手！');
    // e.target 这个可以得到我们点击的对象
    e.target.style.backgroundColor = 'pink';
})
```

> 简单来说，就是利用冒泡原理给父元素设置监听就可以了。

### 七、常用的鼠标事件

#### 1. 常用的鼠标事件

<img src="https://img.zjgsuzjx.top/img/images/2021/06/20/9ce42c7fa6d01e20977eee0d6533f0d8.jpg" alt="9ce42c7fa6d01e20977eee0d6533f0d8.jpg" border="0" />

**禁止鼠标右键菜单**：

```js
// 1. contextmenu 我们可以禁用右键菜单
document.addEventListener('contextmenu', function(e) {
    e.preventDefault();
})
```

**禁止鼠标选中**：

```js
// 2. 禁止选中文字 selectstart
document.addEventListener('selectstart', function(e) {
    e.preventDefault();
})
```

#### 2. 鼠标事件对象

**event**对象代表事件的状态，跟事件相关的一系列信息的集合。现阶段我们主要是用鼠标事件对象 **MouseEvent** 和键盘事件对象 **KeyboardEvent**。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/20/0cedf9f8babfc674616d17540612dd7b.jpg" alt="0cedf9f8babfc674616d17540612dd7b.jpg" border="0" />

```js
// 鼠标事件对象 MouseEvent
document.addEventListener('click', function(e) {
    // 1. client 鼠标在可视区的x和y坐标
    console.log(e.clientX);
    console.log(e.clientY);
    console.log('---------------------');
    // 2. page 鼠标在页面文档的x和y坐标
    console.log(e.pageX);
    console.log(e.pageY);
    console.log('---------------------');
    // 3. screen 鼠标在电脑屏幕的x和y坐标
    console.log(e.screenX);
    console.log(e.screenY);
})
```

**跟随鼠标的天使案例**：

```js
//图片要移动距离，而且不占位置，我们使用绝对定位即可
var pic = document.querySelector('img');
document.addEventListener('mousemove', function(e) {
    // 1. mousemove只要我们鼠标移动1px 就会触发这个事件
    // console.log(1);
    // 2.核心原理： 每次鼠标移动，我们都会获得最新的鼠标坐标， 把这个x和y坐标做为图片的top和left 值就可以移动图片
    var x = e.pageX;
    var y = e.pageY;
    console.log('x坐标是' + x, 'y坐标是' + y);
    //3 . 千万不要忘记给left 和top 添加px 单位
    pic.style.left = x - 50 + 'px';
    pic.style.top = y - 40 + 'px';
});
```

### 八、常用的键盘事件

#### 1. 常用键盘事件

<img src="https://img.zjgsuzjx.top/img/images/2021/06/20/8314f934ccef87c2a9bc0593293e0b82.jpg" alt="8314f934ccef87c2a9bc0593293e0b82.jpg" border="0" />

```js
//1. keyup 按键弹起的时候触发
document.addEventListener('keyup', function () {
    console.log('我弹起了');
})
//2. keydown 按键按下的时候触发  能识别功能键
document.addEventListener('keydown', function () {
    console.log('我按下了down');
})
//3. keypress 按键按下的时候触发  不能识别功能键
document.addEventListener('keypress', function () {
    console.log('我按下了press');
})
```

> 注意：三个事件的执行顺序是： **keydown** -- **keypress** --- **keyup**

> 如果使用addEventListener 不需要加 **on**

> onkeypress 和前面2个的区别是，它不识别功能键，比如**左右箭头**，**shift** 等。

#### 2. 键盘事件对象

```JS
// 1. 我们的keyup 和keydown事件不区分字母大小写
// 2. 我们的keypress 事件 区分字母大小写
document.addEventListener('keyup', function(e) {
    // console.log(e);
    console.log('up:' + e.key);
    // 我们可以利用key返回的ASCII码值来判断用户按下了那个键
    if (e.key === 'a') {
        alert('您按下的a键');
    } else {
        alert('您没有按下a键')
    }
})
document.addEventListener('keypress', function(e) {
    // console.log(e);
    console.log('press:' + e.key);
})
```

> 注意：keyCode已经弃用。要使用**key**。

> 注意： onkeydown 和 onkeyup 不区分字母大小写，**onkeypress** 区分字母大小写。

**按下s键光标定位搜索框**：

```js
// 搜索框获得焦点： 使用 js 里面的 focus() 方法
var search = document.querySelector('input');
document.addEventListener('keyup', function(e) {
    // console.log(e.keyCode);
    if (e.key === 's') {
        search.focus();
    }
})
```

**模拟京东快递单号查询**：

```js
// 快递单号输入内容时， 上面的大号字体盒子（con）显示(这里面的字号更大）
// 表单检测用户输入： 给表单添加键盘事件
// 同时把快递单号里面的值（value）获取过来赋值给 con盒子（innerText）做为内容
// 如果快递单号里面内容为空，则隐藏大号字体盒子(con)盒子
var con = document.querySelector('.con');
var jd_input = document.querySelector('.jd');
jd_input.addEventListener('keyup', function() {
    // console.log('输入内容啦');
    if (this.value === '') {
        con.style.display = 'none';
    } else {
        con.style.display = 'block';
        con.innerText = this.value;
    }
})
// 当我们失去焦点，就隐藏这个con盒子
jd_input.addEventListener('blur', function() {
    con.style.display = 'none';
})
// 当我们获得焦点，就显示这个con盒子
jd_input.addEventListener('focus', function() {
    if (this.value !== '') {
        con.style.display = 'block';
    }
})
```

> 注意： keydown 和 keypress 在文本框里面的特点： 他们两个事件触发的时候，文字还 没有落入文本框中。

> keyup事件触发的时候， 文字已经落入文本框里面了

## 十七、BOM 浏览器对象模型

### 一、BOM 概述

#### 1. 什么是 BOM

BOM（Browser Object Model）即**浏览器对象模型**，它提供了独立于内容而与浏览器窗口进行交互的对象，其核心对象是 **window**。

BOM **缺乏标准**，JavaScript 语法的标准化组织是 ECMA，DOM 的标准化组织是 W3C，BOM 最初是**Netscape** 浏览器标准的一部分。

#### 2. BOM 的构成

BOM 比 DOM 更大，它包含 DOM。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/3993c45bbc97d6dc8c9074d022544eef.jpg" alt="3993c45bbc97d6dc8c9074d022544eef.jpg" border="0" />

window 对象是浏览器的**顶级对象**，它具有双重角色。

1. 它是 JS 访问浏览器窗口的一个接口。
2. 它是一个全局对象。定义在**全局作用域**中的变量、函数都会变成 window 对象的**属性**和**方法**。 

在调用的时候可以省略 **window**，前面学习的对话框都属于 **window 对象方法**，如 alert()、prompt() 等。

> 注意：window下的一个特殊属性 window.name

### 二、window 对象的常见事件

#### 1. 窗口加载事件

window.onload 是窗口 (页面）加载事件,当文档内容**完全加载**完成会触发该事件(包括图像、脚本文件、CSS  文件等), 就调用的处理函数。

```js
window.addEventListener('load', function() {
    var btn = document.querySelector('button');
    btn.addEventListener('click', function() {
        alert('点击我');
    })
})
```

**注意**：

- 有了 window.onload 就可以把 JS 代码写到页面元素的**上方**，因为 onload 是等页面内容全部加载完毕， 再去执行处理函数。

- window.onload **传统注册事件方式** 只能写一次，如果有多个，会以**最后一个** window.onload 为准。

- 如果使用 **addEventListener** 则**没有限制**。

```js
document.addEventListener('DOMContentLoaded', function() {
    alert(33);
})
// DOMContentLoaded 是DOM 加载完毕，不包含图片 falsh css 等就可以执行 加载速度比 load更快一些
```

DOMContentLoaded 事件触发时，仅当DOM加载完成，不包括样式表，图片，flash等等。

> 如果页面的图片很多的话, 从用户访问到onload触发可能需要较长的时间, 交互效果就不能实现，必然影响用户的体验，此时用 **DOMContentLoaded** 事件比较合适。

#### 2. 调整窗口大小事件

```js
window.addEventListener('load', function() {
    var div = document.querySelector('div');
    window.addEventListener('resize', function() {
        if (window.innerWidth <= 800) {
            div.style.display = 'none';
        } else {
            div.style.display = 'block';
        }

    })
})
```

**window.onresize** 是调整窗口大小加载事件, 当触发时就调用的处理函数。

> 注意：只要窗口大小发生像素变化，就会触发这个事件；window.innerWidth 当前屏幕的宽度。

### 三、定时器

#### 1. 两种定时器

window 对象给我们提供了 2 个非常好用的方法-定时器。 **setTimeout** 、**setInterval**。

#### 2. setTimeout() 定时器

setTimeout() 方法用于设置一个定时器，该定时器在定时器到期后执行调用函数。

```js
// 第一种写法
setTimeout(function() {
    console.log('时间到了');
}, 2000);
// 第二种写法
function callback() {
    console.log('爆炸了');
}
var timer1 = setTimeout(callback, 3000);
var timer2 = setTimeout(callback, 5000);
// setTimeout('callback()', 3000); // 我们不提倡这个写法
```

> 注意：**window** 可以**省略**；延迟的毫秒数省略默认是 **0**，如果写，必须是**毫秒**；因为定时器可能有很多，所以我们经常给定时器赋值一个**标识符**。

**回调函数callback**：

需要等待时间，时间到了才去调用这个函数，因此称为回调函数。setTimeout()也是回调函数。

**5秒后自动关闭的广告**：

```js
var ad = document.querySelector('.ad');
setTimeout(function() {
    ad.style.display = 'none';
}, 5000);
```

#### 3. 停止 setTimeout() 定时器

clearTimeout()方法取消了先前通过调用 setTimeout() 建立的定时器。

```js
var btn = document.querySelector('button');
var timer = setTimeout(function() {
    console.log('爆炸了');
}, 5000);
btn.addEventListener('click', function() {
    clearTimeout(timer);
})
```

注意：window 可以省略；里面的参数就是定时器的**标识符** 。

#### 4. setInterval() 定时器

setInterval() 方法**重复调用**一个函数，每隔这个时间，就去调用一次回调函数。

```js
// 语法规范：  window.setInterval(调用函数, 延时时间);
setInterval(function() {
    console.log('继续输出');
}, 1000);
```

> 注意：window 可以**省略**；这个调用函数可以直接写函数，或者写函数名；间隔的毫秒数省略默认是 **0**；第一次执行也是间隔毫秒数之后执行，之后每隔毫秒数就执行一次。

**倒计时案例**：

```js
// 1. 获取元素 
var hour = document.querySelector('.hour'); // 小时的黑色盒子
var minute = document.querySelector('.minute'); // 分钟的黑色盒子
var second = document.querySelector('.second'); // 秒数的黑色盒子
var inputTime = +new Date('2019-5-1 18:00:00'); // 返回的是用户输入时间总的毫秒数
countDown(); // 我们先调用一次这个函数，防止第一次刷新页面有空白 
// 2. 开启定时器
setInterval(countDown, 1000);
function countDown() {
    var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
    var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数 
    var h = parseInt(times / 60 / 60 % 24); //时
    h = h < 10 ? '0' + h : h;
    hour.innerHTML = h; // 把剩余的小时给 小时黑色盒子
    var m = parseInt(times / 60 % 60); // 分
    m = m < 10 ? '0' + m : m;
    minute.innerHTML = m;
    var s = parseInt(times % 60); // 当前的秒
    s = s < 10 ? '0' + s : s;
    second.innerHTML = s;
}
```

#### 5. 停止setInterval() 定时器

clearInterval()方法取消了先前通过调用 setInterval()建立的定时器。

```js
var begin = document.querySelector('.begin');
var stop = document.querySelector('.stop');
var timer = null; // 全局变量  null是一个空对象
begin.addEventListener('click', function() {
    timer = setInterval(function() {
        console.log('ni hao ma');

    }, 1000);
})
stop.addEventListener('click', function() {
    clearInterval(timer);
})
```

> 注意：window 可以省略；里面的参数就是定时器的标识符 。

**发送短信**：

```js
// 按钮点击之后，会禁用 disabled 为true 
// 同时按钮里面的内容会变化， 注意 button 里面的内容通过 innerHTML修改
var btn = document.querySelector('button');
var time = 3; // 定义剩下的秒数
btn.addEventListener('click', function() {
    btn.disabled = true;
    var timer = setInterval(function() {
        if (time == 0) {
            // 清除定时器和复原按钮
            clearInterval(timer);
            btn.disabled = false;
            btn.innerHTML = '发送';
        } else {
            btn.innerHTML = '还剩下' + time + '秒';
            time--;
        }
    }, 1000);

})
```

#### 6. this

> 一般情况下this 的最终指向的是那个调用它的对象。

```js
// 1. 全局作用域或者普通函数中this指向全局对象window（ 注意定时器里面的this指向window）
console.log(this);
function fn() {
    console.log(this);
}
window.fn();
window.setTimeout(function () {
    console.log(this);
}, 1000);
// 2. 方法调用中谁调用this指向谁
var o = {
    sayHi: function () {
        console.log(this); // this指向的是 o 这个对象
    }
}
o.sayHi();
var btn = document.querySelector('button');
btn.addEventListener('click', function () {
    console.log(this); // this指向的是btn这个按钮对象
})
// 3. 构造函数中this指向构造函数的实例
function Fun() {
    console.log(this); // this 指向的是fun 实例对象
}
var fun = new Fun();
```

### 四、JS 执行队列

#### 1. JS 是单线程

JavaScript 语言的一大特点就是**单线程**，也就是说，同一个时间只能做一件事。

单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。这样所导致的问题是： 如果 JS 执行的时间过长，这样就会造成页面的**渲染不连贯**，导致页面渲染**加载阻塞**的感觉。

#### 2. 同步和异步

为了解决这个问题，利用多核 CPU 的计算能力，HTML5 提出 Web Worker 标准，允许 JavaScript 脚本创建多个线程。于是，JS 中出现了**同步**和**异步**。

**同步**：

前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是**一致的**、同步的。

**异步**：

你在做一件事情时，因为这件事情会花费很长时间，在做这件事的同时，你还可以去**处理其他**事情。

> 本质区别：这条流水线上各个流程的执行顺序不同。

**同步任务**：

同步任务都在主线程上执行，形成一个执行栈。

**异步任务**：

JS 的异步是通过**回调函数**实现的。一般而言，异步任务有以下三种类型：

1. **普通事件**，如 click、resize 等 
2. **资源加载**，如 load、error 等
3. **定时器**，包括 setInterval、setTimeout 等

异步任务相关回调函数添加到任务队列中（任务队列也称为消息队列）。

#### 3. JS 执行机制

先执行执行栈中的同步任务 **->** 异步任务（回调函数）放入任务队列中 **->** 一旦执行栈中的所有同步任务执行完毕，系统就会按次序读取<u>任务队列</u>中的异步任务，于是被读取的异步任 务结束等待状态，进入执行栈，开始执行。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/9a925d7c230082fde710dee07fa6b979.jpg" alt="9a925d7c230082fde710dee07fa6b979.jpg" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/ee5f2b44847febc44ce9c7ddf5e29d48.jpg" alt="ee5f2b44847febc44ce9c7ddf5e29d48.jpg" border="0" />

> 由于主线程不断的重复获得任务、执行任务、再获取任务、再执行，所以这种机制被称为事件循环（ event loop）

### 五、location 对象

#### 1. 概念

window 对象给我们提供了一个 location 属性用于获取或设置窗体的 URL，并且可以用于**解析 URL** 。 因为这个属性返回的是一个对象，所以我们将这个属性也称为 **location 对象**。

#### 2. URL

**统一资源定位符** (Uniform Resource Locator, URL) 是互联网上标准资源的地址。互联网上的每个文件都有 一个唯一的 URL，它包含的信息指出文件的位置以及浏览器应该怎么处理它。

URL 的一般语法格式为：

```html
protocol://host[:port]/path/[?query]#fragment
```

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/1b3a7f37485a52771f1529e2dd2509fe.jpg" alt="1b3a7f37485a52771f1529e2dd2509fe.jpg" border="0" />

####  3. location 对象的属性

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/df342541bc401ba2677f5fad7ada48d9.jpg" alt="df342541bc401ba2677f5fad7ada48d9.jpg" border="0" />

**5秒钟之后自动跳转页面**：

```js
var btn = document.querySelector('button');
var div = document.querySelector('div');
btn.addEventListener('click', function() {
    location.href = 'http://www.zjgsuzjx.top';
})
var timer = 5;
setInterval(function() {
    if (timer === 0) {
        location.href = 'http://www.itcast.cn';
    } else {
        div.innerHTML = '您将在' + timer + '秒钟之后跳转到首页';
        timer--;
    }
}, 1000);
```

**获取 URL 参数数据**：

```html
<!--login页面-->
<form action="index.html">
    用户名： <input type="text" name="uname">
    <input type="submit" value="登录">
</form>
```

```js
//index页面
console.log(location.search); // ?uname=andy
// 1.先去掉？  substr('起始的位置'，截取几个字符);
var params = location.search.substr(1); // uname=andy
console.log(params);
// 2. 利用=把字符串分割为数组 split('=');
var arr = params.split('=');
console.log(arr); // ["uname", "ANDY"]
var div = document.querySelector('div');
// 3.把数据写入div中
div.innerHTML = arr[1] + '欢迎您';
```

#### 4. location 对象的方法

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/215158b726444705d6d308f5da9364e2.jpg" alt="215158b726444705d6d308f5da9364e2.jpg" border="0" />

```js
var btn = document.querySelector('button');
btn.addEventListener('click', function() {
    // 记录浏览历史，所以可以实现后退功能
    location.assign('http://www.itcast.cn');
    // 不记录浏览历史，所以不可以实现后退功能
    location.replace('http://www.itcast.cn');
    // 刷新页面
    location.reload();
})
```

#### 5. navigator 对象

navigator 对象包含有关浏览器的信息，它有很多属性，我们最常用的是 userAgent，该属性可以返回由客户机发送服务器的 user-agent 头部的值。

```js
if ((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS |Symbian|Windows Phone)/i))) {
    window.location.href = ""; //手机
} else {
    window.location.href = ""; //电脑
}
```

#### 6. history 对象

window 对象给我们提供了一个 history 对象，与浏览器历史记录进行交互。该对象包含用户（在浏览器窗口中） 访问过的 URL。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/00eaa0d14e2af2cafb83a8610368bf1d.jpg" alt="00eaa0d14e2af2cafb83a8610368bf1d.jpg" border="0" />

```js
var btn = document.querySelector('button');
btn.addEventListener('click', function() {
    // 前进
    // history.forward();
    history.go(1);
})

var btn = document.querySelector('button');
btn.addEventListener('click', function() {
      // 后退
      // history.back();
      history.go(-1);
 })
```

## 十八、PC 端网页特效

### 一、元素偏移量 offset 系列

#### 1. offset 概述

offset 翻译过来就是**偏移量**， 我们使用 **offset** 系列相关属性可以**动态的**得到该元素的位置（偏移）、大小等。

**offset 系列常用属性**：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/f7cf3c0d0112ce136a82dbe59001477b.jpg" alt="f7cf3c0d0112ce136a82dbe59001477b.jpg" border="0" />

> 注意： 返回的数值都不带单位

```js
// offset 系列
var father = document.querySelector('.father');
var son = document.querySelector('.son');
// 1.可以得到元素的偏移 位置 返回的不带单位的数值  
console.log(father.offsetTop);
console.log(father.offsetLeft);
// 它以带有定位的父亲为准  如果么有父亲或者父亲没有定位 则以 body 为准
console.log(son.offsetLeft);
var w = document.querySelector('.w');
// 2.可以得到元素的大小 宽度和高度 是包含padding + border + width 
console.log(w.offsetWidth);
console.log(w.offsetHeight);
// 3. 返回带有定位的父亲 否则返回的是body
console.log(son.offsetParent); // 返回带有定位的父亲 否则返回的是body
console.log(son.parentNode); // 返回父亲 是最近一级的父亲 亲爸爸 不管父亲有没有定位
```

#### 2. offset 与 style 区别

**offset**：

- offset 可以得到任意样式表中的样式值
- offset 系列获得的数值是没有单位的
- offsetWidth 包含padding+border+width
- offsetWidth 等属性是**只读属性**，只能获取不能赋值
- 所以，我们想要获取元素大小位置，用offset更合适

**style**：

- style 只能得到行内样式表中的样式值
- style.width 获得的是带有单位的字符串
- style.width 获得不包含padding和border 的值
- style.width 是**可读写属性**，可以获取也可以赋值
- 所以，我们想要给元素更改值，则需要用style改变

**获取鼠标在盒子内的坐标**：

```js
var box = document.querySelector('.box');
box.addEventListener('mousemove', function(e) {
    var x = e.pageX - this.offsetLeft;
    var y = e.pageY - this.offsetTop;
    this.innerHTML = 'x坐标是' + x + ' y坐标是' + y;
})
```

**模态框拖拽**：

```js
// 1. 获取元素
var login = document.querySelector('.login');
var mask = document.querySelector('.login-bg');
var link = document.querySelector('#link');
var closeBtn = document.querySelector('#closeBtn');
var title = document.querySelector('#title');
// 2. 点击弹出层这个链接 link  让mask 和login 显示出来
link.addEventListener('click', function () {
    mask.style.display = 'block';
    login.style.display = 'block';
})
// 3. 点击 closeBtn 就隐藏 mask 和 login 
closeBtn.addEventListener('click', function () {
    mask.style.display = 'none';
    login.style.display = 'none';
})
// 4. 开始拖拽
// (1) 当我们鼠标按下， 就获得鼠标在盒子内的坐标
title.addEventListener('mousedown', function (e) {
    var x = e.pageX - login.offsetLeft;
    var y = e.pageY - login.offsetTop;
    // (2) 鼠标移动的时候，把鼠标在页面中的坐标，减去 鼠标在盒子内的坐标就是模态框的left和top值
document.addEventListener('mousemove', move)
    function move(e) {
        login.style.left = e.pageX - x + 'px';
        login.style.top = e.pageY - y + 'px';
    }
    // (3) 鼠标弹起，就让鼠标移动事件移除
   document.addEventListener('mouseup', function () {
 document.removeEventListener('mousemove', move);
    })
})
```

**仿京东放大镜**：

[建议自己做](https://www.bilibili.com/video/BV1Sy4y1C7ha?p=300&spm_id_from=pageDriver)

### 二、元素可视区 client 系列

client 翻译过来就是客户端，我们使用 client 系列的相关属性来获取元素可视区的相关信息。

> 和offset的区别在于不包含边框。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/0d1be4fe84288d89f9972a4d08108af9.jpg" alt="0d1be4fe84288d89f9972a4d08108af9.jpg" border="0" />

### 三、元素滚动 scroll 系列

#### 1. 元素 scroll 系列属性

scroll 翻译过来就是滚动的，我们使用 scroll 系列的相关属性可以动态的得到该元素的大小、滚动距离等。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/b3cee4541278141c05edd618127022b4.jpg" alt="b3cee4541278141c05edd618127022b4.jpg" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/8878c1836a4b5113e65bce4980b82915.jpg" alt="8878c1836a4b5113e65bce4980b82915.jpg" border="0" />

#### 2. 页面被卷去的头部

如果浏览器的高（或宽）度不足以显示整个页面时，会自动出现滚动条。当滚动条向下滚动时，页面上面被隐藏掉的高度，我们就称为页面被卷去的头部。滚动条在滚动时会触发 onscroll 事件。

**仿淘宝固定右侧侧边栏**：

```js
//1. 获取元素
var sliderbar = document.querySelector('.slider-bar');
var banner = document.querySelector('.banner');
// banner.offestTop 就是被卷去头部的大小 一定要写到滚动的外面
var bannerTop = banner.offsetTop
// 当我们侧边栏固定定位之后应该变化的数值
var sliderbarTop = sliderbar.offsetTop - bannerTop;
// 获取main 主体元素
var main = document.querySelector('.main');
var goBack = document.querySelector('.goBack');
var mainTop = main.offsetTop;
// 2. 页面滚动事件 scroll
document.addEventListener('scroll', function () {
    // window.pageYOffset 页面被卷去的头部
    // 3 .当我们页面被卷去的头部大于等于了 172 此时 侧边栏就要改为固定定位
    if (window.pageYOffset >= bannerTop) {
        sliderbar.style.position = 'fixed';
        sliderbar.style.top = sliderbarTop + 'px';
    } else {
        sliderbar.style.position = 'absolute';
        sliderbar.style.top = '300px';
    }
    // 4. 当我们页面滚动到main盒子，就显示 goback模块
    if (window.pageYOffset >= mainTop) {
        goBack.style.display = 'block';
    } else {
        goBack.style.display = 'none';
    }

})
```

**三大系列总结**：

1. offset系列 经常用于获得元素位置 offsetLeft offsetTop
2. client 经常用于获取元素大小 clientWidth clientHeight
3. scroll 经常用于获取滚动距离 scrollTop scrollLeft
4. 注意页面滚动的距离通过window.pageXOffset 获

**mouseenter 鼠标事件**：

当鼠标移动到元素上时就会触发 **mouseenter** 事件 

类似 **mouseover**，它们两者之间的<u>差别</u>是：**mouseover** 鼠标经过自身盒子会触发，经过子盒子还会触发。 **mouseenter** 只会经过自身盒子触发

之所以这样，就是因为mouseenter**不会冒泡**

跟**mouseenter**搭配 鼠标离开 **mouseleave** 同样不会冒泡。

### 四、动画函数封装

#### 1. 动画实现原理

**核心原理**：通过定时器 setInterval() 不断移动盒子位置。

**实现步骤**：

1. 获得盒子当前位置
2. 让盒子在当前位置加上1个移动距离
3. 利用定时器不断重复这个操作
4. 加一个结束定时器的条件
5. 注意此元素需要添加定位，才能使用element.style.left

```js
var div = document.querySelector('div');
var timer = setInterval(function() {
    if (div.offsetLeft >= 400) {
        // 停止动画 本质是停止定时器
        clearInterval(timer);
    }
    div.style.left = div.offsetLeft + 1 + 'px';
}, 30);
```

#### 2. 动画函数简单封装

> 注意函数需要传递2个参数，动画对象和移动到的距离。

```js
// 简单动画函数封装obj目标对象 target 目标位置
function animate(obj, target) {
    var timer = setInterval(function() {
        if (obj.offsetLeft >= target) {
            // 停止动画 本质是停止定时器
            clearInterval(timer);
        }
        obj.style.left = obj.offsetLeft + 1 + 'px';

    }, 30);
}
var div = document.querySelector('div');
var span = document.querySelector('span');
// 调用函数
animate(div, 300);
animate(span, 200);
```

#### 3. 给不同元素记录不同定时器

如果多个元素都使用这个动画函数，每次都要var 声明定时器。我们可以给不同的元素使用不同的定时器（自己专门用自己的定时器）。

> 核心原理：利用 JS 是一门动态语言，可以很方便的给当前对象添加属性。

```js
function animate(obj, target) {
    // 当我们不断的点击按钮，这个元素的速度会越来越快，因为开启了太多的定时器
    // 解决方案就是 让我们元素只有一个定时器执行
    // 先清除以前的定时器，只保留当前的一个定时器执行
    clearInterval(obj.timer);
    obj.timer = setInterval(function() {
        if (obj.offsetLeft >= target) {
            // 停止动画 本质是停止定时器
            clearInterval(obj.timer);
        }
        obj.style.left = obj.offsetLeft + 1 + 'px';
    }, 30);
}
var div = document.querySelector('div');
var span = document.querySelector('span');
var btn = document.querySelector('button');
// 调用函数
animate(div, 300);
btn.addEventListener('click', function() {
    animate(span, 200);
})
```

#### 4. 缓动效果原理

缓动动画就是让元素运动速度有所变化，最常见的是让速度慢慢停下来。

思路：

1. 让盒子每次移动的距离慢慢变小，速度就会慢慢落下来。
2. **核心算法**： (目标值 - 现在的位置 ) / 10 做为每次移动的距离步长
3. 停止的条件是： 让当前盒子位置等于目标位置就停止定时器
4. 注意步长值需要**取整** 

```js
function animate(obj, target) {
    // 先清除以前的定时器，只保留当前的一个定时器执行
    clearInterval(obj.timer);
    obj.timer = setInterval(function() {
        // 步长值写到定时器的里面
        var step = Math.ceil((target - obj.offsetLeft) / 10);
        if (obj.offsetLeft === target) {
            clearInterval(obj.timer);
        }
        // 把每次加1 这个步长值改为一个慢慢变小的值  步长公式：(目标值 - 现在的位置) / 10
        obj.style.left = obj.offsetLeft + step + 'px';
    }, 15);
}
var span = document.querySelector('span');
var btn = document.querySelector('button');
btn.addEventListener('click', function() {
    animate(span, 500);
})
```

#### 5. 多个目标值之间移动

可以让动画函数从 800 移动到 500。 当我们点击按钮时候，判断步长是正值还是负值。

```js
var step = (target - obj.offsetLeft) / 10;
step = step > 0 ? Math.ceil(step) : Math.floor(step);
```

#### 6. 动画函数添加回调函数

**回调函数原理**：函数可以作为一个**参数**。将这个函数作为参数传到另一个函数里面，当那个函数执行完之后， 再执行传进去的这个函数，这个过程就叫做**回调**。

> 回调函数写的位置：定时器结束的位置。

```js
animate(span, 800, function() {
    // alert('你好吗');
    span.style.backgroundColor = 'red';
});
```

#### 7. 封装到单独JS文件里面

因为以后经常使用这个动画函数，可以单独封装到一个JS文件里面，使用的时候引用这个JS文件即可。

### 五、常见网页特效案例

#### 1. 网页轮播图

[建议自己做一下](https://www.bilibili.com/video/BV1Sy4y1C7ha?p=325&spm_id_from=pageDriver)

**节流阀**：

防止轮播图按钮连续点击造成播放过快。

节流阀**目的**：当上一个函数动画内容执行完毕，再去执行下一个函数动画，让事件无法连续触发。 

核心**实现思路**：利用回调函数，添加一个变量来控制，锁住函数和解锁函数。

```js
// 开始设置一个变量 var flag = true;
// If(flag) {flag = false; do something} 关闭水龙头
// 利用回调函数 动画执行完毕， flag = true 打开水龙头
```

#### 2. 返回顶部

```js
goBack.addEventListener('click', function() {
    // 里面的x和y 不跟单位的 直接写数字即可
    // window.scroll(0, 0);
    // 因为是窗口滚动 所以对象是window
    animate(window, 0);
});
// 动画函数
function animate(obj, target, callback) {
    clearInterval(obj.timer);
    obj.timer = setInterval(function() {
        var step = (target - window.pageYOffset) / 10;
        step = step > 0 ? Math.ceil(step) : Math.floor(step);
        if (window.pageYOffset == target) {
            clearInterval(obj.timer);
            callback && callback();
        }
        window.scroll(0, window.pageYOffset + step);
    }, 15);
}
```

#### 3. 筋头云案例

```js
window.addEventListener('load', function() {
    // 1. 获取元素
    var cloud = document.querySelector('.cloud');
    var c_nav = document.querySelector('.c-nav');
    var lis = c_nav.querySelectorAll('li');
    // 2. 给所有的小li绑定事件 
    // 这个current 做为筋斗云的起始位置
    var current = 0;
    for (var i = 0; i < lis.length; i++) {
        // (1) 鼠标经过把当前小li 的位置做为目标值
        lis[i].addEventListener('mouseenter', function() {
            animate(cloud, this.offsetLeft);
        });
        // (2) 鼠标离开就回到起始的位置 
        lis[i].addEventListener('mouseleave', function() {
            animate(cloud, current);
        });
        // (3) 当我们鼠标点击，就把当前位置做为目标值
        lis[i].addEventListener('click', function() {
            current = this.offsetLeft;
        });
    }
})
```

## 十九、移动端网页特效

### 一、触屏事件

#### 1. 概述

移动端浏览器兼容性较好，我们不需要考虑以前 JS 的兼容性问题，可以放心的使用原生 JS 书写效果，但是移动端也有自己独特的地方。比如触屏事件**touch**（也称触摸事件），Android 和 IOS 都有。

```js
// 1. 获取元素
// 2. 手指触摸DOM元素事件
var div = document.querySelector('div');
div.addEventListener('touchstart', function() {
    console.log('我摸了你');
});
// 3. 手指在DOM元素身上移动事件
div.addEventListener('touchmove', function() {
    console.log('我继续摸');
});
// 4. 手指离开DOM元素事件
div.addEventListener('touchend', function() {
    console.log('轻轻的我走了');
});
```

#### 2. 触摸事件对象（TouchEvent）

TouchEvent 是一类描述手指在触摸平面（触摸屏、触摸板等）的状态变化的事件。

touchstart、touchmove、touchend 三个事件都会各自有事件对象。

触摸事件对象重点我们看三个常见对象列表：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/22/5103586df7f1cd7027c52613001520af.jpg" alt="5103586df7f1cd7027c52613001520af.jpg" border="0" />

> 因为平时我们都是给元素注册触摸事件，所以重点记住 targetTouches

#### 3. 移动端拖动元素

拖动元素三步曲：

（1）触摸元素 **touchstart**： 获取手指初始坐标，同时获得盒子原来的位置

（2）移动手指 **touchmove**： 计算手指的滑动距离，并且移动盒子

（3）离开手指 **touchend**

> 注意：手指移动也会触发滚动屏幕所以这里要阻止默认的屏幕滚动 e.preventDefau

```js
var div = document.querySelector('div');
var startX = 0; //获取手指初始坐标
var startY = 0;
var x = 0; //获得盒子原来的位置
var y = 0;
div.addEventListener('touchstart', function(e) {
    //  获取手指初始坐标
    startX = e.targetTouches[0].pageX;
    startY = e.targetTouches[0].pageY;
    x = this.offsetLeft;
    y = this.offsetTop;
});
div.addEventListener('touchmove', function(e) {
    //  计算手指的移动距离： 手指移动之后的坐标减去手指初始的坐标
    var moveX = e.targetTouches[0].pageX - startX;
    var moveY = e.targetTouches[0].pageY - startY;
    // 移动我们的盒子 盒子原来的位置 + 手指移动的距离
    this.style.left = x + moveX + 'px';
    this.style.top = y + moveY + 'px';
    e.preventDefault(); // 阻止屏幕滚动的默认行为
});
```

### 二、移动端常见特效

#### 1. 移动端轮播图

[建议自己做一下。]([JavaScript基础语法-dom-bom-js-es6新语法-jQuery-数据可视化echarts黑马pink老师前端入门基础视频教程(500多集)持续_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Sy4y1C7ha?p=340&spm_id_from=pageDriver))

> 配合CSS3使用更好。另外手指可以滑动图片。

#### 2. classList 属性

classList属性是HTML5新增的一个属性，返回元素的类名。但是ie10以上版本支持。

> 该属性用于在元素中添加，移除及切换 CSS 类。

```js
// classList 返回元素的类名
var div = document.querySelector('div');
// console.log(div.classList[1]);
// 1. 添加类名  是在后面追加类名不会覆盖以前的类名 注意前面不需要加.
div.classList.add('three');
// 2. 删除类名
div.classList.remove('one');
// 3. 切换类
var btn = document.querySelector('button');
btn.addEventListener('click', function() {
    document.body.classList.toggle('bg');
})
```

> 注意以上方法里面，所有类名都不带点

### 三、移动端常用开发插件

#### 1. 什么是插件

JS 插件是 **js 文件**，它遵循一定规范编写，方便程序展示效果，拥有特定功能且方便调用。如轮播图和瀑布流插件。

> 特点：它一般是为了解决某个问题而专门存在，其功能单一，并且比较小。

#### 2. 插件的使用

引入 js 插件文件、按照规定语法使用。

#### 3. Swiper 插件的使用

中文官网地址： https://www.swiper.com.cn/ 

#### 4. 其他移动端常见插件

superslide： http://www.superslide2.com/

iscroll： https://github.com/cubiq/iscrol

### 四、移动端常用开发框架

#### 1. 框架概述

**框架**，顾名思义就是一套架构，它会基于自身的特点向用户提供一套较为完整的解决方案。框架的控制权在框架本身，使用者要按照框架所规定的某种规范进行开发。

**插件**一般是为了解决某个问题而专门存在，其功能单一，并且比较小。

前端常用的框架有 **Bootstrap**、**Vue**、Angular、**React** 等。既能开发PC端，也能开发移动端

前端常用的移动端插件有 swiper、superslide、iscroll等。 插件一般是为了解决某个问题而专门存在，其功能单一，并且比较小。

> 框架： 大而全，一整套解决方案
>
> 插件： 小而专一，某个功能的解决方

#### 2. Bootstrap

Bootstrap JS插件**使用步骤**：

1. 引入相关js 文件
2. 复制HTML 结构
3. 修改对应样式
4. 修改相应JS 参数

## 二十、本地存储

随着互联网的快速发展，基于网页的应用越来越普遍，同时也变的越来越复杂，为了满足各种各样的需求，会经常性<u>在本地存储大量的数据</u>，HTML5规范提出了相关解决方案。

### 一、本地存储特性

1、数据存储在用户**浏览器**中

2、设置、读取方便、甚至页面刷新**不丢失**数据

3、容量较大，sessionStorage约5M、localStorage约20M

4、只能存储**字符串**，可以将对象JSON.stringify() 编码后存储

### 二、sessionStorage

> 1、生命周期为**关闭浏览器**窗口
>
> 2、在同一个窗口(页面)下数据可以共享
>
> 3、以键值对的形式存储使用

```js
var ipt = document.querySelector('input');
var set = document.querySelector('.set');
var get = document.querySelector('.get');
var remove = document.querySelector('.remove');
var del = document.querySelector('.del');
set.addEventListener('click', function() {
    // 当我们点击了之后，就可以把表单里面的值存储起来
    var val = ipt.value;
    sessionStorage.setItem('uname', val);
    sessionStorage.setItem('pwd', val);
});
get.addEventListener('click', function() {
    // 当我们点击了之后，就可以把表单里面的值获取过来
  console.log(sessionStorage.getItem('uname'));

});
remove.addEventListener('click', function() {
    sessionStorage.removeItem('uname');
});
del.addEventListener('click', function() {
    // 当我们点击了之后，清除所有的
    sessionStorage.clear();
});
```

### 三、localStorage

> 1、声明周期**永久生效**，除非手动删除 否则关闭页面也会存在
>
> 2、可以多窗口（页面）共享（同一浏览器可以共享）
>
> 3、以键值对的形式存储使用

```js
var ipt = document.querySelector('input');
var set = document.querySelector('.set');
var get = document.querySelector('.get');
var remove = document.querySelector('.remove');
var del = document.querySelector('.del');
set.addEventListener('click', function() {
    var val = ipt.value;
    // 存储数据
    localStorage.setItem('username', val);
})
get.addEventListener('click', function() {
    //获取数据
  console.log(localStorage.getItem('username'));
})
remove.addEventListener('click', function() {
    // 删除数据
    localStorage.removeItem('username');
})
del.addEventListener('click', function() {
    // 删除所有数据
    localStorage.clear();
})
```

**记住用户名**：

```js
// ① 把数据存起来，用到本地存储
// ② 关闭页面，也可以显示用户名，所以用到localStorage
// ③ 打开页面，先判断是否有这个用户名，如果有，就在表单里面显示用户名，并且勾选复选框
// ④ 当复选框发生改变的时候 change事件
// ⑤ 如果勾选，就存储，否则就移除
var username = document.querySelector('#username');
var remember = document.querySelector('#remember');
if (localStorage.getItem('username')) {
    username.value = localStorage.getItem('username');
    remember.checked = true;
}
remember.addEventListener('change', function () {
    if (this.checked) {
        localStorage.setItem('username', username.value)
    } else {
        localStorage.removeItem('username');
    }
})
```



