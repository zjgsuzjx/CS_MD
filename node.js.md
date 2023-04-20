> 💥此MD/PDF/HTML文档由 [@竹梦者也](https://www.zjgsuzjx.top/)编辑制作，不可贩卖❌。仅供学习交流使用，下载后切勿随意传播。转载麻烦加上出处~
>
> 📌欢迎在留言区提供修改建议~
>
> 💌本文内容和代码来自于`tianyu`老师的Node教程
>
> 
>
> ✅2021.7.12	 @竹梦者也(https://www.zjgsuzjx.top) 
>
> ✅2021.7.18	 更新v1.1，完善了模块化内容







## 一、Node.js

### 一、基本使用

#### 1. 概念

Node.js 是一个基于 Chrome V8 引擎的 `JavaScript` 运行环境。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/07/c958254e333bb78272c98b9835dbdd04.png" alt="c958254e333bb78272c98b9835dbdd04.png" border="0" width="40%"/>

> 使得让JS代码在本地也能运行，从而能够操作本地的文件。原理是将JS代码转译为C/C++代码，从而能够实现socket（网络编程）、http、文件系统、etc（编译环境）、事件循环模型、异步操作。

#### 2. 特点

**优点**：

1) 异步非阻塞的I/O（I/O线程池）

2) 特别适用于I/O密集型应用（频繁I/O操作）

3) 事件循环机制

4) 单线程（成也单线程，败也单线程）

5) 跨平台

**缺点**：

1)  回调函数嵌套太多、太深（俗称回调地狱）

2)  单线程，处理不好CPU 密集型任务（Java解决高并发是<u>提升配置</u>，Node解决高并发是用<u>回调函数</u>；CPU每个请求太慢时，会造成Node排队时间过长）

> <u>CPU密集型与I/O密集型的区别：</u>
>
> CPU密集型：需要过多的判断，事情不明确。
>
> I/O密集型：不需要过多的判断，事情明确。

#### 3. 与浏览器端区别

在**浏览器端**：js由BOM、DOM、ES规范组成。

在**Node端**：js只由ES（所有规范）和global（Node内置属性，相当于window）组成。

#### 4. 安装

https://nodejs.org/zh-cn/

左边是正式服，右边是测试服。

安装完成之后，打开命令行窗口，输入`node -v`查看当前node版本。

#### 5. 环境配置

https://www.cnblogs.com/zhouyu2017/p/6485265.html

> 环境配置的目的是为了在cmd中能够直接使用指令。如node、yarn等等。

#### 6. 用Node运行JS

**方法1**：

在cmd里，cd到JS文件所在文件夹。再输入`node xxx.js`。

**方法2**：

打开我的电脑到指定文件夹，在路径中直接输入`cmd`并回车，后面跟上面同理。

**方法3**：

在webstorm里配置好node环境，直接右键运行js文件。

> File ---> Settings ---> Languages & Frameworks ---> Node.js and NPM

**方法4**：

按住shift + 右键，点击在此处打开命令行。再输入`node xxx.js`。

### 二、模块化

#### 1. 概念

**模块化**指的就是将一个大的功能拆分为一个一个小的模块，通过不同的模块的组合来实现一个大功能。

> Node中使用的是`CommonJS`规范来实现的模块化，前端使用的模块化规范是`AMD`和`CMD`。

#### 2. CommonJS

CommonJS 是一套模块化规范，它包含：模块、二进制、Buffer、字符集编码、I/O流、进程环境、文件系统、套接字、单元测试、Web服务器网关接口、包管理等。

> 补充：CommonJS是唯一一个可以在双端（浏览器、node）运行的模块化规范。
>
> 补充2：服务器端模块的加载时**同步**的。
>
> 补充3：暴露的本质是`module.exports`所指向的那个**对象**。

在CommonJS模块规范中，`module.exports`和`exports.xxx`不能混用。如果混用则以`module.exports`为主。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/17/9511253dbb927fdc02293da0d76475cc.png" alt="9511253dbb927fdc02293da0d76475cc.png" border="0" width="50%"/>

**模块引用**

通过require()函数来引入外部的模块。

```js
var a = require("../a");
var math = require("math");
```

> 它需要一个模块的标识作为参数，返回一个**对象**表示引入的模块
>
> **补充**：在引入的同时可以解构赋值。
>
> **注意**：引入第三方模块时，直接写包名；引入自定义模块时，要写路径。

**模块使用**

模块暴露的是一个对象，所以在使用时就当作对象来使用，如：

```js
math.test();
math.data;
```

**模块定义**

1) 在node中一个js文件就是一个模块

2) 在node中每一个模块中的代码都是运行在一个独立的函数中的，

3) 默认情况下模块内部代码对于外部来说都是**不可见**的，可以通过两种方式向外部暴露变量和函数

> a.可以通过将**变量**和**函数**设置为 `exports` 的属性来暴露变量和函数

```js
exports.name = "xxx";  // 追加属性
exports.sayHello = function(){...}; // 追加属性
```

> b.也可以通过module.exports来向外部暴露变量和函数

```js
module.exports.name = "xxx"; // 追加属性
module.exports.sayHello = function(){...}; // 追加属性 
module.exports = { // 改变指向
    a:"xxx",
    b:"xxx"
};
// module.exports = value
```

**模块标识**

1) 引入外部模块时，需要通过模块的标识进行引入

2) 对于自定义的文件模块，模块的标识就是文件的路径（绝对路径、以 . 或 .. 开头的相对路径）

例子："`./a`" "`../b`"

3) 对于下载的模块或系统模块模块的标识就是文件的名字如"`fs`" "`express`"

**module.exports和exports的区别**

`exports`变量是对`module`的`exports`属性的引用，我们在向`exports`中添加属性时，本质上是在向`module.exports`中添加属性。module.exports 可以直接通过赋值的形式来暴露内容。`exports` 不能直接赋值，只能通过.`的形式添加属性`。

> 如果是简单的暴露属性，使用`exports`就好，引入模块使用方式：m1.属性名
>
> 如果需要向外暴露一个构造函数，使用`module.exports`，引入模块使用方式：m1

**node中的函数**

输入以下代码在node用运行。

```js
console.log(arguments.callee.toString())
```

会出现：

```js
function (exports, require, module, __filename, __dirname){
	// js中的内容
}
```

这个函数是所有模块都有的，node编译时往其中注入5个参数：

`exports`      暴露模块

`require`       引入模块

`module`       exports属性暴露模块

`__filename`    文件的绝对路径

`__dirname`    文件夹的绝对路径

##### # 浏览器端

在浏览器端有特殊的目录要求。index页面是必须的。

浏览器不认识`require`。需要借助第三方包`browserify`。

**安装**：`npm install -g browserify`

**执行**：`browserify (输入文件路径) -o （输出文件路径）`，注意路径问题。

> 浏览器没有引入的先后顺序。

#### 3. ES6模块化

只支持浏览器端。

共有三种暴露方式，分别暴露、统一暴露、默认暴露。

##### # 暴露

**分别暴露**：

```js
export let data=1;
export function demo() {
    console.log(data)
}
```

**统一暴露**：

```js
function demo2() {
  console.log('我是module2里的demo2函数',arr)
}

function test2() {
  console.log('我是module2里的test2函数',arr)
}

export {demo2,test2}
```

**默认暴露**

```js
export default {
  school:'atguigu',
  price:'15K'
}
```

##### # 引入

```js
//引入module1，module1是【分别暴露】的
import {data,demo1,test1} from './module1' // 不是解构赋值
//引入module2,module2是【统一暴露】的
import {demo2,test2} from './module2'
//【引入module3,module3是默认暴露的】
import module3 from './module3'
// 引入第三方，用的是默认暴露
import uniq from 'uniq'
```

> **备注**：分别暴露和统一暴露使用频率较少，因为有**命名冲突**。

##### # 进阶使用

```js
// 另外一种写法，收集成对象，默认暴露不推荐这么引入
import * as haha from './module1'


//统一暴露(完整版写法)
export {
  demo2 as haha1, //暴露的同时可以，赋一个别名
  test2 as haha2
}
```

> 备注：暴露可以混着用，引入时默认暴露必须排在前面。

```js
//引入module4，module4里用了多种暴露的方式
import module4,{arr0,bar,foo,str,student,d1} from './module4'
```

##### # Babel

浏览器不认识ES6的模块化语法。需要一个第三方包`Babel`。可以将ES6语法转成ES5语法，并且将`jsx`语法转为`js`语法。

全局安装：`npm install babel-cli browserify -g`

局部安装：`npm install babel-preset-es2015 -D`

创建`.babelrc`文件：在根目录下创建，内容如下：

```
{
    "presets": ["es2015"]
}
```

命令：`babel (输入文件夹路径) -d (输出文件夹路径)`

`browserify (输入文件路径) -o (输出文件路径)`

> 备注：成功后还会自动启动严格模式。

#### 4. AMD模块化

全称Asynchronous Module Definition（异步模块定义）。

专门用于浏览器端，模块的加载是异步的。

需要`require.js`文件。https://requirejs.org/

**基本语法**：

```js
/*
* 定义一个没有依赖的module1
* */

define(function () {
  //数据-----私有数据（只读）
  let data = 'atguigu'
  //获取数据的方法
  function getDataL() {
    return data.toLowerCase()
  }
  function getDataU() {
    return data.toUpperCase()
  }
    // 对象简写方式
  return {getDataL,getDataU}
})
```

```js
/*
* 定义一个有依赖的module2,module2依赖于module1，要使用module1中的数据--data
* */

define(['module1'],function (module1) {
  let msg = '0719就业顺利！'

  //获取module1中的data和module2中的msg
  function getDataAndMsg() {
    return module1.getDataL() + msg
  }

  return getDataAndMsg
})
```

```js
/*
* 在AMD模块化中，主js文件(入口文件)需要写一个特殊的【配置对象】。
* */
requirejs.config({
  baseUrl: './js', //如果配置了baseUrl，项目的根目录了就是index.html所在目录

  //在项目中所有用到的模块，都要在这里注册
  paths: {
    module1: '/modules/module1',
    module2: '/modules/module2',
    jquery: '/lib/jquery-1.10.1' // 必须是小写
  }
});

requirejs(['module2','jquery'],function (m2,$) {
  console.log(m2());
  $('body').css('background','skyblue')
});
```

**html引入**：

```html
<!--AMD模块化中，主页面中也要用特殊的引入方式-->
<script data-main="./js/app.js" src="./js/lib/require.js"></script>
```

> 总结：很老的项目还在用
>

#### 5. CMD模块化

阿里自己写的模块，全称Common Module Definition（）

**基本语法**：

```js
/*
* 定义一个没有依赖的模块，module1
* */
define(function (require,exports,module) {
  let data = '--------module1---------'
  function getData() {
    console.log(data)
  }
  module.exports = {getData}
})
```

```js
/*
* 定义一个没有依赖的模块，module2
* */
define(function (require,exports,module) {
  let data = '--------module2---------'
  function getData() {
    console.log(data)
  }
  module.exports = {getData}
})
```

```js
/*
* 定义一个没有依赖的模块，module3
* */
define(function (require,exports,module) {
  let data = '--------module3---------'
  function getData() {
    console.log(data)
  }
  module.exports = {getData}
})
```

```js
/*
* 定义一个有依赖的模块，module4,依赖于module2和module3
* */
define(function (require,exports,module) {
  let data = '--------module4---------'
  //引入module2-----同步引入
  let module2 = require('./module2')
  module2.getData()
  //引入module3-----异步引入
  require.async('./module3',function (m3) {
    m3.getData()
  })
  function getData() {
    console.log(data)
  }
  module.exports = {getData}
})
```

**汇总**：

```js
/*
* 主js文件，用于汇总各个模块
* */
define(function (require) {
  let module1 = require('./module1')
  let module4 = require('./module4')
  module1.getData()
  module4.getData()
})
```

**使用sea.js**：

```html
<script type="text/javascript" src="js/libs/sea.js"></script>
<script type="text/javascript">
  seajs.use('./js/modules/main')
</script>
```

> 输出顺序为：2---1---4---3

### 三、包和包管理器

#### 1. package包

Node.js的包基本遵循`CommonJS`规范，包将一组相关的模块组合在一起，形成一组完整的工具。

> 举例：类似电脑上的一个文件夹，包含了某些特定的文件，并且符合某些特定的结构，就是一个包。

包由包结构和包描述文件两个部分组成。

1) **包结构**：用于组织包中的各种文件

2) **包描述文件**：描述包的相关信息，以供外部读取分析

##### # 包结构

包实际上就是一个压缩文件，解压以后还原为目录。符合CommonJS规范的目录，应该包含如下文件：

1) `package.json`  描述文件（**必要**）

2) `bin`  可执行二进制文件（可选）

3) `lib`  js代码（可选）

4) `doc` 文档（可选）

5) `test` 单元测试（可选）

##### # 包描述文件

包描述文件用于表达非代码相关的信息，它是一个`JSON`格式的文件：`package.json`

包描述文件包含以下字段：`name`、`version`、`description`、`keywords`、`maintainers`、`contributors`、`bugs`、`licenses`、`repositories`、`dependencies`（生产依赖）、`homepage`、`os`、`cpu`、`engine`、`builtin`、`directories`、`implements`、`scripts`、`author`、`bin`、`main`、`devDependencies`（开发依赖）。

##### # 创建一个包

输入命令：`npm init`

包名要求：不能有中文、大写字母、尽量不能与其它包同名。

#### 2. NPM

全称：`Node Package Manager` , Node的包管理器。

##### # 作用

通过NPM可以对Node的包进行搜索、下载、安装、删除、上传。

##### # 常用指令

**搜索**：`npm search xxxx`；或者www.npmjs.com

**安装**：`npm install xxxx -g`（全局安装）== 等同于`npm i xxxx -g`

`npm install xxxx -D`(安装包并写入到开发依赖中)

> 注意**开发依赖**和**生产依赖**的区别：写代码时才用到的库，就是开发依赖；项目上线给其它人用时的库，就是生产依赖，如jquery等等。

`npm i xxx@x.x.x`（安装x.x.x版本的包）

`npm i`（安装package.json中声明的所有包）

**移除**：`npm remove xxx`（在node_module中删除xxx包，同时删除package.json声明）

**其它**：`npm view xxxx versions`（查看npm仓库中xxx包的所有版本信息）

`npm ls xxxx`（查看当前安装的xxx包的版本）

#### 3. cnpm

##### # 概念

它是淘宝对国外npm服务器的一个完整镜像版本，也就是淘宝 NPM 镜像。可以加速下载。

https://npm.taobao.org/

##### # 安装

**第一种**

直接安装：安装淘宝提供的cnpm，并更改服务器地址为淘宝的国内地址。

`npm install -g cnpm --registry=https://registry.npm.taobao.org`,以后安装可以直接采用cnpm代替npm。

缺点：会造成npm和cnpm两种指令共存，会有bug。

**第二种**

替换npm仓库地址为淘宝镜像地址（推荐）。

命令：`npm config set registry https://registry.npm.taobao.org`，查看是否成功：`npm config get registry`。

#### 4. Yarn

##### # 概念

`yarn`是Facebook开源的新的包管理器，可以用来代替`npm`。

##### # 特点

有缓存；没有自己的仓库地址，使用的是npm仓库地址。

##### # 安装

`npm install yarn -g`

##### # 修改Yarn的全局安装和缓存位置

在CMD命令行中执行

```
#1.改变 yarn 全局安装位置
yarn config  set global-folder "你的磁盘路径"
#2.然后你会在你的用户目录找到 `.yarnrc` 的文件，打开它，找到 `global-folder` ，改为 `--global-folder`
#这里是我的路径
yarn config  set global-folder "D:\Software\yarn\global"
```

```
#2. 改变 yarn 缓存位置
yarn config set cache-folder "你的磁盘路径"
#这里是我的路径
yarn config set cache-folder "D:\Software\yarn\cache"
```

在我们使用全局安装包的时候，会在“D:\Software\yarn\global”下生成 `node_modules\bin`目录

我们需要将`D:\Software\yarn\global\node_modules\.bin` 整个目录添加到系统环境变量中去，否则通过`yarn`添加的全局包 在`cmd`中是找不到的。

检查当前yarn的bin的位置：`yarn global bin`

检查当前yarn的全局安装位置：`yarn global dir`

> 随后跟配置npm一样配置环境变量。

##### # 常用指令

`yarn global add xxxx`（全局下载指定包）

`yarn global remove xxxx`（删除全局依赖包）

`yarn info xxxx`（查看某个包的信息）

`yarn init -y`（初始化项目）

### 四、Buffer缓冲器

#### 1. 概念

- 它是一个**类似于数组**的对象，用于存储数据（存储的是二进制数据）。
- Buffer的效率很高，存储和读取很快，它是直接对计算机的内存进行操作。
- Buffer的大小一旦确定了，不可修改。
- 每个元素占用内存的大小为1字节(byte)。
- Buffer 是Node中的非常核心的模块，无需下载、无需引入，直接即可使用

#### 2. 使用

一共有三种创建方式。

##### # 第一种

```js
let bf=new Buffer(10);
```

> 备注：性能特别差。特点是在堆里开辟空间，同时会清理要回收的空间为己用。

##### # 第二种

```js
let bf=new Buffer.alloc(10);
```

> 备注：性能比new Buffer()稍强一点。特点是在堆中开辟一段空间，且这个空间没有被使用过。

##### # 第三种

```js
let bf=new Buffer.allocUnsafe(10);
```

> 备注：性能最好。特点是在堆里随意开辟空间，可能是别人用过的。

**问题**

<u>为什么输出的不是二进制？</u>

> 输出的是16进制，但是存储的是二进制，输出的时候会自动转换为16进制

<u>为什么第三种输出的不为空？</u>

> 在堆里开辟空空间，可能残留着别人用过的数据。

#### 3. 数据存入实例

```js
let bf=Buffer.from('hello world!');
console.log(bf); // <Buffer 68 65 6c 6c 6f 20 77 6f 72 6c 64 21>
```

输出的16进制，可以用`bf.toString()`方法转为字符串。之所以是16进制，是因为存入的不一定是字符串，也可以是媒体文件如视频、音乐等等。

### 五、fs文件系统

#### 1. 概念

全称为`file system`，所谓的文件系统，就是对计算机中的文件进行增删改查等操作。它是一个服务器的基础，在Node中通过fs模块来操作文件系统。

#### 2. 使用

fs模块是Node的核心模块，不需要下载，直接引入即可使用。

```js
// 引入fs模块
let fs=require('fs');
```

> fs中的大部分方法都为我们提供了两个版本：

**同步方法**：带sync的方法

同步方法会阻塞程序的执行；同步方法通过返回值返回结果。

**异步方法**：不带sync的方法

异步方法不会阻塞程序的执行；异步方法都是通过回调函数来返回结果的。

##### # 简单文件的写入

**语法**：

```js
fs.writeFile(file, data[, options], callback)
```

`file`：要写入的文件路径+文件名+后缀

`data`：要写入的数据

`options`：配置**对象**（可选参数）

--`encoding`：设置文件的编码方式，默认值: 'utf8'
--`mode`：设置文件的操作权限，默认值: 0o666
--`flag`：打开文件要执行的操作。 默认值: 'w'。
--`signal`：允许中止正在进行的写入文件

`callback`：回调函数

`err`：错误对象

**例子**：

```js
let fs=require('fs');
fs.writeFile('./demo.txt','helloworld!',(err)=>{
    if(err){
        console.log('写入失败',err);
    }else{
        console.log('写入成功');
    }
});
```

##### # 流式文件写入

**语法**：

```js
fs.createWriteStream(path[, options])
```

`path`：要写入文件的路径+文件名+文件后缀

`options`；配置对象（可选参数）

--`flags`：同上
--`encoding`：同上
-`fd`：文件统一标识符，Linux下文件标识符
--`mode`：同上
--`autoClose`：自动关闭--文件，默认值：true
--`emitClose`：关闭-—-文件，默认值：true
--`start`：写入文件的起始位（偏移量）

**例子**：

```js
let fs = require('fs');
// 创建一个可写流
let ws = fs.createWriteStream('./demo.txt');
// 监测流的状态
ws.on('open',function () {
    console.log('可写流打开了');
})
ws.on('close',function () {
    console.log('可写流关闭了');
})
// 使用可写流写入数据
ws.write('helloworld!\n');
ws.write('welcome\n');
// 关闭
//ws.close();  如果node8版本中，会有问题
ws.end(); // node8版本中可以正常使用
```

##### # 简单文件读取

**语法**：

```js
fs.readFile(path[, options], callback)
```

`path`：要读取文件的路径+文件名+后缀

`options`：配置对象（可选）

`callback`：回调

**例子**：

```js
let fs = require('fs');
fs.readFile('./demo.txt',function (err,data) {
    if(err){
        console.log(err);
    }else{
        console.log(data.toString()); // 如果是非文本文件，不能这样写
    }
})
```

> 简单文件写入和简单文件读取，都是一次性把所有要读取或要写入的内容加到内存中，容易造成内存泄露。

##### # 流式文件读取

**语法**：

```js
fs.createReadStream(path[, options])
```

`path`：要读取文件的路径+文件名+后缀
`options`：同上
--`flags`：同上
--`encoding`：同上
--`fd`：同上
--`mode`：同上
--`autoClose`：同上
--`emitclose`：同上
--`start`：起始偏移量
--`end`：结束的偏移量
--`highwaterMark`：每次读取数据的大小，默认是64*1024

**例子**：

```js
let {createReadStream} = require('fs'); // 解构赋值
// 创建一个可读流
let rs=createReadStream('./demo.txt');
// 只要用到了流，就必须监测流的状态
rs.on('open',function () {
    console.log('可读流打开了');
})
rs.on('close',function () {
    console.log()
})
// 给可写流绑定一个data事件，就会触发可读流自动读取内容
rs.on('data',function (data) {
    // Buffer实例的length属性，表示该Buffer实例占用内存空间的大小
    console.log(data.length); // 输出的是6556，每次读取64KB的内容
})
```

**边读边写的流失例子**：

```js
let {createReadStream,createWriteStream} = require('fs');
let rs=createReadStream('./demo.txt',{
    highWaterMark:10*1024*1024
    // start:60000,
    // end:120000  可以截取片段，视频图片不适用
});
let ws=createWriteStream('./demo1.txt');
rs.on('open',function () {
    console.log('可读流打开了');
})
rs.on('close',function () {
    console.log('可读流关闭了');
    ws.close(); // 必须在这里关闭阀
})
ws.on('open',function () {
    console.log('可写流打开了');
})
ws.on('close',function () {
    console.log('可写流关闭了')
})
rs.on('data',function (data) {
    console.log(data.length);
    ws.write(data);
})
```

## 二、数据库

### 一、基本概念

#### 1. 含义

数据库（`DataBase`）是按照数据结构来组织、存储和管理数据的仓库。

#### 2. 用途

我们的程序都是在内存中运行的，一旦程序运行结束或者计算机断电，程序运行中的数据都会丢失。所以我们就需要将一些程序运行的数据持久化到硬盘之中，以确保数据的安全性。而数据库就是数据持久化的最佳选择。

> 说白了，数据库就是存储数据的仓库。

#### 3. 分类

##### # 关系型数据库（RDBS）

**代表有**：`MySQL`(⭐，轻量)、`Oracle`(⭐，甲骨文)、`DB2`、`SQL` `Server`(微软，大学上课才用)

**特点**：关系紧密，都是表

<img src="https://img.zjgsuzjx.top/img/images/2021/07/08/386c1628cac70025eb3ef0261307ef44.png" alt="386c1628cac70025eb3ef0261307ef44.png" border="0" />

**优点**：

1、易于维护：都是使用表结构，格式一致

2、使用方便：通用，可用于复杂查询（全是SQL语句）

3、高级查询：可用于一个表以及多个表之间非常复杂的查询

**缺点**：

1、<u>读写性能比较差</u>，尤其是海量数据的高效率读写

2、有固定的表结构，字段不可随意更改，<u>灵活度稍欠</u>

3、高并发读写需求，传统关系型数据库来说，<u>硬盘I/O</u>是一个很大的瓶颈

**举例**：

- Excel文件->数据库
- sheet页签->表
- 列头->字段(唯一标识，不允许修改 **主键**)
- 一行->一条数据

##### # 非关系型数据库（NoSQL）

**代表有**：`MongoDB`、`Redis`（高速缓存，大数据用）

**特点**：关系不紧密，有文档，有键值对

<img src="https://img.zjgsuzjx.top/img/images/2021/07/08/ef3804bc68296afaab581adbd5f6908b.png" alt="ef3804bc68296afaab581adbd5f6908b.png" border="0" />

**优点**：

1、格式灵活：存储数据的格式可以是key,value形式

2、速度快：nosql可以内存作为载体，而关系型数据库只能使用硬盘

3、易用：nosql数据库部署简单

**缺点**：

1、<u>不支持sql</u>（结构化查询语句），学习和使用成本较高

2、不支持<u>事务</u>（ACID特性，所以不能用于支付交易）

3、复杂查询时语句<u>过于繁琐</u>

### 二、MongoDB

#### 1. 简介

MongoDB是为快速开发互联网Web应用而设计的数据库系统。

MongoDB的设计目标是极简、灵活、作为Web应用栈的一部分。

MongoDB的数据模型是面向文档的，所谓文档是一种类似于JSON的结构，简单理解MongoDB这个数据库中存的是各种各样的JSON。（BSON）

#### 2. 安装

**最新社区版**：https://www.mongodb.com/try/download/community

**教程**：https://www.jianshu.com/p/e963d0e0bb94

或者https://blog.csdn.net/yuxiaohe1/article/details/111317947

> 4.4以上已经自动配置好开机自动启动了，无需另外配置

#### 3. 安装图形化工具

studio3t：https://studio3t.com/download/（需要破解）

Navicat Premium 15：http://www.navicat.com.cn/download/navicat-premium（需要破解，破解教程https://mp.weixin.qq.com/s/g2myLey2Of0V0_YqwvnWpQ）

#### 4. Navicat使用教程

https://www.jb51.net/article/206956.htm

> 在导航栏处的**查询**按钮可以使用编辑器，有代码高亮和提示，支持多行语句运行。

> **查看->显示隐藏项目**  可以显示被隐藏的数据库

<img src="https://img.zjgsuzjx.top/img/images/2021/07/09/da779c6f4666b9c5ee66f7a34cecd296.md.png" alt="da779c6f4666b9c5ee66f7a34cecd296.png" border="0" />

#### 5. MongoDB的使用

##### # 简介

数据库（`database`）：数据库是一个仓库，在仓库中可以存放集合。

集合（`collection`）：集合类似于JS中的数组，在集合中可以存放文档。说白了，集合就是一组文档。非常类似于`JSON`，因此称为`BSON`。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/09/4f0fcfa42b0602b76a46fd00aef92680.png" alt="4f0fcfa42b0602b76a46fd00aef92680.png" border="0" />

文档（`document`）：文档数据库中的最小单位，我们存储和操作的内容都是文档。类似于JS中的对象，在MongoDB中每一条数据都是一个文档。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/09/c44065c7bdd3f213c881193fcba8335d.png" alt="c44065c7bdd3f213c881193fcba8335d.png" border="0" width="50%"/>

##### # 基本命令

- 显示所有的数据库：`show dbs`或`show databases`（注意没有集合的数据库不会显示）

- 切换到指定的数据库：`use 数据库名`（没有的话会自动创建）

- 显示当前所在的数据库：`db`


- 删除当前数据库：`db.dropDatabase()`

- 显示当前数据库中的所有集合：`show collections`


- 删除当前集合：`db.collection.drop()`


##### # 操作命令

> 在`MongoDB`，<u>数据库</u>和<u>集合</u>都不需要创建，当我们向集合或数据库中第一次插入文档时，集合和数据库会**自动创建**。

- 向集合中插入文档：`db.<collection>.insert(doc)`

**如**：`db.stus.insert({name:"sunwukong",age:18})`

- 查询集合中的文档：`db.<collection>.find()`

**如**：`db.stus.find()`

#### 6. 数据库的CRUD

> CRUD指的是数据库的增删改查（create、delete、update、read）。

查询网址: https://docs.mongodb.com/manual/reference/method/js-collection/

**-C create（新增数据）**：

`db.集合名.insert（文档对象）`

`db.集合名.insertOne（文档对象）`

`db.集合名.insertMany（[文档对象，文档对象]）`

如：

```sql
db.students.insert({name:'zhangsam',age:18,grade:66,sex:'男'});
db.students.insertOne({name:'lisi',age:20,grade:50,sex:'女'});
db.students.insertMany([{name:'wangwu',age:19,grade:80,sex:'男'},{name:'xsan',age:17,grade:30,sex:'女'}]);
```

> `insert`和`insertOne`的底层代码是一样的

**-R read（查询数据）**：

`db.集合名.find（查询条件[，投影]）`

举例：

`db.students.find({age:18})`，查找年龄为18的所有信息类例

`db.students.find({age:18,name:'jack"})`，查找年龄为18且名字为jack的学生

> 投影：过滤掉不想要的数据，只保留想要展示的数据。`_id`比较特殊，要单独写。

`db.students.find({},{_id:0,name:0})`，过滤掉id和name

`db.students.find({},{age:1})`，只保留age

<u>补充</u>：`db.集合名.findOne(查询条件[,投影])`，默认只要找到到一个，提高效率。

<u>常用操作符</u>：

- <，<=，>，>=，==对应为：`$lt $lte $gt $gte $ne` 

举例：`db.集合名.find({age:{$gte:20}})`，年龄是大于等于20的

- 逻解或：使`in`或`or`

查找年龄为18或20的学生

举例：`db.students.find({age:($in:[18,20]}})`

举例：`db.students.find(($or:[{age:18},{age:20}]})`

- 逻解非：`$nin`

举例：`db.students.find({age:{$nin:[19,17]}})`，不是19也不是17

- 正则匹配：

举例：`db.students.find({name:/^T/})`，查找所有T开头的名字

- $where能写函数：

```sql
db.students.find({$where:function(){
	return this.name === 'zhangsam' && this.age === 18
}})
```

**-U update（更新数据）**：

`db.集合名.update(查询条件,要更新的内容[,配置对象])`

// 如下写法会将更新内容替换掉整个文档对象，但_id不受影响，**慎用**

举例：`db.students.update({name:'zhangsan'},{age:19})`

// 使用`$set`修改指定内容，其他数据不变，不过只能匹配一个

举例：`db.students.update({name:'zhangsan"},{$set:{age:19}})`

// 修改多个文档对象，匹配多个，把所有匹配到的年龄都替换为19

举例：`db.students.update((name:'zhangsan'},{$set:{age:19}},{multi:true})`

补充：`db.集合名.updateOne(查前条件,要更新的内容(,配置对象])`

`db.集合名.updateMany(查询条件,要更新的内容[,配置对象])`

**-D delete（删除数据）**：

`db.集合名.remove(查询条件)`

// 删除所有年龄小于等于19的学生
举例：`db.students.remove({age:($lte:19}})`

#### 7. Mongoose

##### # 简介

`Mongoose`是一个对象文档模型（ODM）库，它对Node原生的MongoDB模块进行了进一步的优化封装，并提供了更多的功能。

> `mongoDB`：一个数据库品牌的名字
>
> `mongod`：启动数据库的命令
>
> `mongo`：连接数据库的命令
>
> `mongoose`：Node平台下，一个知名的用于帮助开发者连接mongoDB的包

##### # 优势

- 可以为文档创建一个模式结构（`Schema`）
- 可以对模型中的对象/文档进行验证
- 数据可以通过类型转换转换为对象模型
- 可以使用中间件来应用业务逻辑挂钩
- 比Node原生的MongoDB驱动更容易

##### # 使用

**下载**：

`yarn global add mongoose`或者`npm i mongoose -g`

**连接**：

```js
// 为什么使用mongoose？可以在node平台下，更加简单、高效、安全、稳定的操作mongoDB
// 当引入第三方库的时候，如果在本文件夹内没有找到node_modules，找外层文件夹，直到根目录
let mongoose = require('mongoose');
mongoose.connect('mongodb://localhost:27017/hello1',{
    useNewUrlParser:true, // 使用一个新的URL解析器
    useUnifiedTopology:true // 使用统一的新的拓扑结构
})
// 绑定数据库连接的监听
mongoose.connection.on('open',function (err) {
    if(err){
        console.log('数据库连接失败！',err);
    }else{
        console.log('数据库连接成功！');
        // 操作数据库
        console.log('操作数据库')
    }
})
```

##### # CRUD

**-C create（新增数据）**：

```js
let mongoose = require('mongoose');
mongoose.set('useCreateIndex',true); // 创建一个新的索引器
mongoose.connect('mongodb://localhost:27017/hello1', {
    useNewUrlParser: true, // 使用一个新的URL解析器
    useUnifiedTopology: true // 使用统一的新的拓扑结构
})
mongoose.connection.on('open', function (err) {
    if (err) {
        console.log('数据库连接失败！', err);
    } else {
        console.log('数据库连接成功！');
        // 引入模式对象
        let Schema = mongoose.Schema;
        // 创建约束对象
        let studentsRule = new Schema({
            stu_id: {
                type: String,
                required: true,
                unique: true // 限制唯一
            },
            name: {
                type: String,
                required: true
            },
            age: {
                type: Number,
                required: true
            },
            sex: {
                type: String, // 限制性别必须为字符串
                required: true // 限制为必填项
            },
            hobby: [String], // 限制爱好只能为数组，数组中的每一项必须为字符串
            info: Schema.Types.Mixed, // 接受所有类型
            date: {
                type: Date,
                default: Date.now() // 默认值
            },
            enable_flag: {
                type: String,
                default: 'Y'
            }
        })
        // 创建模型对象
        let stuModel = mongoose.model('students', studentsRule) // 用于生成某个集合所对应的模型对象
        // CRUD
        stuModel.create({ // 创建文档对象
            stu_id:'002',
            name:'张飞',
            age:18,
            sex:'男',
            hobby:['打代码','看电影'],
            info:'美男子'
        },function (err,data) {
            if(!err){
                console.log(data);
            }else{
                console.log(err);
            }
        })
    }
})
```

> 没有数据库时，会自动创建，其中`__v`是mongo自带的。成功后的图如下：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/09/c77bdcb5a41f0d06007c19080ab0c011.png" alt="c77bdcb5a41f0d06007c19080ab0c011.png" border="0" />

> 之后记得右键刷新数据库。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/09/b210d7878ea94a76c7a7766287c3bfd6.png" alt="b210d7878ea94a76c7a7766287c3bfd6.png" border="0" />

**-R read（查询数据）**：

```js
// 查询操作
// find方法，返回的是一定是一个数组；若查询结果为空，则返回空数组
stuModel.find({name:'吕布'},function (err,data) {
    if(!err) console.log(data);
    else console.log(err);
})
// findOne方法，若有结果返回一个对象，反之返回一个null
```

**-U update（更新数据）**：

```js
// 更新
// updateOne为匹配一个修改，updateMany为匹配多个修改
stuModel.updateOne({name:'吕布'},{age:22},function (err,data) { 
    if(!err) console.log(data);
    else console.log(err);
})
```

**-D delete（删除数据）**：

```js
// 删除，也可以deleteOne
stuModel.deleteMany({age:22},function (err,data) {
    if(!err) console.log(data);
    else console.log(err);
})
```

**投影**：

```js
// 投影
stuModel.findOne({name: '张飞'}, {age: 1, _id: 0}, function (err, data) {
    if (!err) console.log(data);
    else console.log(err);
})
```

> 注意：规则执行过一次之后，只会越来越严格，无法变宽；Mongo提供了字符串自动转译功能，但是对于无法转数字的字符串还是会报错的。

#### 8. mongoose的模块化

**app.js**：

```js
let mongoose = require('mongoose');
let db = require('./db');
let stuModel = require('./studentModel');
db(function (err) {
    if (err) console.log(err);
    else {
        // 新增操作
        stuModel.create({ // 创建文档对象
            stu_id: '003',
            name: '张飞',
            age: 18,
            sex: '男',
            hobby: ['打代码', '看电影'],
            info: '美男子'
        }, function (err, data) {
            if (!err) {
                console.log(data);
            } else {
                console.log(err);
            }
        })
    }
})
```

**db.js**：

```js
let mongoose = require('mongoose');
mongoose.set('useCreateIndex', true);
const DB_NAME = 'hello1'; // 定义常量，方便日后直接修改，是数据库名字
const PORT = 27017;
const IP = 'localhost';

function connectMongo(callback) {
    mongoose.connect(`mongodb://${IP}:${PORT}/${DB_NAME}`, {
        useNewUrlParser: true, // 使用一个新的URL解析器
        useUnifiedTopology: true // 使用统一的新的拓扑结构
    });
    mongoose.connection.on('open', function (err) {
        if (err) {
            console.log('数据库连接失败！', err);
            callback('connect failed');
        } else {
            console.log('数据库连接成功！');
            callback();
        }
    });
}
module.exports = connectMongo; // 函数暴露
```

**studentModel.js**：

```js
let mongoose = require('mongoose');
let Schema = mongoose.Schema;
let studentsRule = new Schema({
    stu_id: {
        type: String,
        required: true,
        unique: true // 限制唯一
    },
    name: {
        type: String,
        required: true
    },
    age: {
        type: Number,
        required: true
    },
    sex: {
        type: String, // 限制性别必须为字符串
        required: true // 限制为必填项
    },
    hobby: [String], // 限制爱好只能为数组，数组中的每一项必须为字符串
    info: Schema.Types.Mixed, // 接受所有类型
    date: {
        type: Date,
        default: Date.now() // 默认值
    },
    enable_flag: {
        type: String,
        default: 'Y'
    }
})
module.exports = mongoose.model('students', studentsRule) // 模块暴露，students是集合名字
```

> 由于回调函数是在最后执行的，所以不能直接反馈。所以要通过这种回调函数传参、暴露函数的方法来实现模块化，也可以用promise来实现，但还没学习。

## 三、Express

### 一、原生Node服务器

#### 1. 服务器搭建

```js
// 引入Node内置的http模块
let http=require('http');
// 创建服务对象
let server=http.createServer(function (request,response) {
    // 设置响应头
    response.setHeader('content-type','text/html;charset=utf-8')
    response.end('<h1>hello world!你好世界！<h1>');
})
// 指定服务器运行的端口号（绑定端口监听）
server.listen(3000,function (err) {
    if(err) console.log(err);
    else console.log();
})
```

#### 2. 服务器响应

```js
let http=require('http');
/*形如：key=value&key=value...的编码形式称为urlencoded编码形式
请求地址里携带这种形式的参数，叫做：查询字符串参数
* */
// 引入一个新模块
let qs=require('querystring');
let server=http.createServer(function (request,response) {
    // 获取客户端携带过来的urlencoded编码形式的参数
    let params=request.url.split('?')[1];
    let objParams=qs.parse(params); // 转对象
    let {name,age}=objParams; // 解构赋值
    response.setHeader('content-type','text/html;charset=utf-8')
    response.end(`<h1>hello world!${name}你好世界！${age}<h1>`);
})
server.listen(3000,function (err) {
    if(err) console.log(err);
    else console.log();
})
```

运行服务器之后，在浏览器输入http://127.0.0.1:3000/?name=zhangsan&age=18，会出现*hello world!zhangsan你好世界！18*

### 二、Express使用

#### 1. 概念

Express 是一个基于 Node.js 平台的**极简**、**灵活**的 web 应用开发框架，它提供一系列强大的特性，帮助你快速创建各种 Web 和移动设备应用。

> 简单来说Express就是运行在node中的用来搭建服务器的模块。

#### 2. 下载

`npm i express -g`

#### 3. 搭建服务器

```js
const express=require('express');
const app=express();
app.listen(3000,function (err) {
    if(err) console.log(err);
    else console.log('启动啦');
})
```

#### 4. Route路由

##### # 概念

路由是指如何定义应用的端点（URIs）以及如何响应客户端的请求。

路由是由一个 `URI`、`HTTP` 请求（GET、POST等）和若干个句柄组成的。

##### # 组成部分

我们可以将路由定义为三个部分

第一部分：HTTP请求的方法（get或post）

第二部分：URI路径

第三部分：回调函数

##### # 实例

```js
const express=require('express');
const app=express();
// (1)配置路由---对请求的url进行分类，服务器根据分类决定交给谁去处理
// (2)路由可以理解为：一组组key-value的组合，key：请求方式+URL路径，value：回调函数
// (3)根据路由定义的顺序，依次定义好路由，随后放入一个类似数组的结构。匹配成功不再匹配。
app.get('/',function (request,response) {
    console.log(request.query); // 封装好的响应头
    response.send('我是主页');
})
// 一级路由
app.get('/food',function (request,response) {
    response.send('我是美食');
})
// 二级路由
app.get('/food/f1',function (request,response) {
    response.send('我是美食---1');
})
app.post('/',function (request,response) {
    response.send('我是post的主页');
})
// 指定服务器运行的端口号
app.listen(3000,function (err) {
    if(err) console.log(err);
    else console.log('启动啦');
})
```

可以配合html的form表单来测试：

```html
<form action="http://127.0.0.1:3000/" method="get">
    <input type="text" name="name">
    <input type="password" name="age">
    <input type="submit">
</form>
```

##### # Request对象

`Request`对象是路由回调函数中的第一个参数，代表了用户发送给服务器的请求信息。要先引入`express`。

> 通过`Request`对象可以读取用户发送的请求包括`URL`地址中的查询字符串中的参数，和`post`请求的请求体中的参数。

| 属性/方法         | 描述                                                         |
| ----------------- | ------------------------------------------------------------ |
| request.query     | 获取**查询字符串**的参数，拿到的是一个对象                   |
| request.params    | 获取`get`请求**参数路由**的参数，拿到的是一个对象            |
| request.body      | 获取`post`请求体，拿到的是一个对象（要借助一个<u>中间件</u>） |
| request.get(xxxx) | 获取请求头中指定`key`对应的`value`                           |

参数路由有特殊语法：

```js
app.get('/meishi/:id',function (req,res) { // 写作:id，接收所有虚拟路由
    let {id}=req.params
    res.send(`我是${id}商家`)
})
```

##### # Response对象

`Response`对象是路由回调函数中的第二个参数，代表了服务器发送给用户的响应信息。

> 通过`Response`对象可以设置响应报文中的各个内容，包括响应头和响应体。

| 属性/方法                  | 描述                                                  |
| -------------------------- | ----------------------------------------------------- |
| response.send()            | 给浏览器做出一个响应                                  |
| response.end()             | 给浏览器做出一个响应（不会自动追加响应头）            |
| response.download()        | 告诉浏览器下载一个文件                                |
| response.sendFile()        | 给浏览器发送一个文件  ，必须传递绝对路径，`__dirname` |
| response.redirect()        | 重定向到一个新的地址（url）                           |
| response.set(header,value) | 自定义响应头内容                                      |
| response.get()             | 获取响应头指定key对应的value  ,但拿不到Date           |
| res.status(code)           | 设置响应状态码  ，尽量不要自己设置                    |

> 备注：若有多个响应则以 response.send为主

#### 5. 中间件

##### # 简介

中间件（Middleware） 是一个函数，它可以访问请求对象（`request`）, 响应对象（`response`）, 和 web 应用中处于请求-响应循环流程中的中间件，一般被命名为 `next` 的变量。

> 补充：银行系统和安全系统等需要安全功能的场合会大量使用中间件。

##### # 功能

1) 执行任何代码。

2) 修改请求和响应对象。

3) 终结请求-响应循环。（让一次请求得到响应）

4) 调用堆栈中的下一个中间件或路由。

##### # 分类

1) 应用级（全局）中间件（过滤非法的请求，例如防盗链）

​	--第一种写法：`app.use((request,response,next)=>{})`

​	--第二种写法：使用函数定义

2) 第三方中间件（通过`npm`下载的中间件，例如`body-parser`）

3) 内置中间件（`express`内部封装好的中间件）

4) 路由器中间件 （`Router`）

##### # 应用层中间件

```js
// 使用应用级（全局）中间件----所有请求的第一扇门
app.use((request,response,next)=>{
    // response.send('我是中间件给的响应');
    // 图片防盗链
    if(request.get('Referer')){ // 有Referer源才会执行
        // 切割返回的字符串
        let miniReferer=request.get('Referer').split('/')[2];
        if(miniReferer==='localhost:63347'){
            next(); // 放行
        }else{
            // 发生了盗链
            response.sendFile(__dirname+'err.png');
        }
    }else{
        next();
    }
})

app.get('/picture', function (request,response) {
    response.sendFile(__dirname+'demo.jpg');
})
```

> 备注：以上代码要在app.js里。不是来自端口号63347就不给通过。

**优化方案**：

```js
// 定义函数
function gruadpic(request, response, next) {
	// 放上面的ifelse内容
}
app.get('/picture' , gruadpic , function (request,response) {
    response.sendFile(__dirname+'demo.jpg');
})
```

> 好处：这就是中间件的含义。只有请求该地址的时候才会做出判断，避免了很多无用功的判断。

##### # 第三方中间件

需要下载一个**中间件**：`npm i body-parser -g`

```js
const express = require('express');
// 引入中间件
const bodyParse=require('body-parser')
const app = express();
// 这个中间件规定的必要的语句
app.use(bodyParse.urlencoded({extended:true}));
// 一级路由
app.post('/food', function (request, response) {
    console.log(request.body);
    response.send('我是美食');
})
app.listen(3000, function (err) {
    if (err) console.log(err);
    else console.log('启动啦');
})
```

> 由此就可以用body拿到post请求过来的数据。

##### # 内置中间件

不用使用`body-parser`，只要加上这一句express内置的方法。就可以实现上面例子的结果。

```js
app.use(express.urlencoded({extended:true}));
```

暴露静态资源可以把所有该目录下的html页面交出去，比如http://loaalhost:3000/meishi.html，就可以访问public目录下的meishi.html。

```js
// 使用内置中间件去暴露静态资源--一次性把所指定的文件夹内的资源全部交出去
app.use(express.static(__dirname + '/public'));
```

##### # 注册登录页面案例

校验数据的合法性：（<u>一般是**前台**和**后台**同时验证</u>）

1.校验成功
->去数据库中查找该邮箱是否法册过
法册过：提示用户邮第已被占用。
未注册：写入数据库

2.校验失败
->提示用户具体哪里输入的不正确

**server.js**:

```js
const express = require('express');
const app = express();
app.use(express.urlencoded({extended: true}));
app.use(express.static(__dirname + '/public'));

const usersModel = require('./model/usersModel');
const db = require('./db/db');
db(() => {
    // 用于展示登录界面的路由，无其他任何逻辑 ----- UI路由
    app.get('/login', function (req, res) {
        res.sendFile(__dirname + '/public/login.html');
    })
    app.get('/register', function (req, res) {
        res.sendFile(__dirname + '/public/register.html');
    })

    app.post('/register', function (req, res) {
        const {email, nick_name, password, re_password} = req.body
        //校验邮件的正则表达式
        const emailReg = /^[a-zA-Z0-9_]{4,20}@[a-zA-Z0-9]{2,10}\.com$/
        //校验昵称的正则表达式
        const nickNameReg = /[\u4e00-\u9fa5]/gm
        //校验密码的正则表达式
        const passwordReg = /^[a-zA-Z0-9_@#.+&]{6,20}$/
        if (!emailReg.test(email)) {
            res.send('邮箱格式不合法，用户名必须4-20位，主机名必须2-10位');
        } else if (!nickNameReg.test(nick_name)) {
            res.send('昵称格式不合法，必须为中文')
        } else if (!passwordReg.test(password)) {
            res.send('密码格式不合法，必须6-20')
        } else if (password !== re_password) {
            res.send('两次输入密码不一致')
        } else {
            //去数据库中查询该邮箱是否注册过
            usersModel.findOne({email}, function (err, data) { // 注意，email是简写
                if (data) {
                    //引入计数模块--当达到一个敏感的阈值，触发安全性机制。
                    console.log(`邮箱为${email}的用户注册失败，因为邮箱重复`)
                    res.send('该邮箱已被注册，请更换邮箱')
                } else {
                    usersModel.create({email, nick_name, password}, function (err) {
                        if (!err) {
                            //如果写入成功了
                            console.log(`邮箱为${email}的用户注册成功`)
                            res.send('注册成功了')
                        } else {
                            //引入报警模块，当达到敏感阈值，触发报警。
                            console.log(err)
                            res.send('您当前的网络状态不稳定，稍后重试')
                        }
                    })
                }
            })
        }
    })
    //用于处理用户的登录请求，有很多业务逻辑(校验数据的有效性等) -------- 业务路由
    app.post('/login',function (req,res) {
        //1.获取输入
        const {email,password}=req.body
        //2.准备正则
        const emailReg = /^[a-zA-Z0-9_]{4,20}@[a-zA-Z0-9]{2,10}\.com$/
        const passwordReg = /^[a-zA-Z0-9_@#.+&]{6,20}$/
        if(!emailReg.test(email)){
            res.send('邮箱格式不合法，用户名必须4-20位，主机名必须2-10位')
        }else if(!passwordReg.test(password)){
            res.send('密码格式不合法，必须6-20')
        }else{
            //3.去数据库中查找：
            usersModel.findOne({email,password},(err,data)=>{
                if(err){
                    //引入报警模块，当达到敏感阈值，触发报警。
                    console.log(err)
                    res.send('网络不稳定，稍后重试')
                    return
                }
                if(data){
                    // 登录就重定向
                    res.redirect('https://www.baidu.com')
                    return
                }
                res.send('用户名或密码输入错误！')
            })
        }
    })
    //绑定端口监听
    app.listen(3000, function (err) {
        if (err) console.log(err);
        else console.log('启动啦');
    })
})
```

**login.html**:

```html
<form action="http://localhost:3000/register" method="post">
    邮箱：<input type="email" name="email" id="email"><br><br>
    昵称：<input type="text" name="nick_name"><br><br>
    密码：<input type="password" name="password"><br><br>
    重复密码：<input type="password" name="re_password"><br><br>
    <input type="submit">
</form>
```

**register.html**:

```html
<form action="http://localhost:3000/register" method="post">
    邮箱：<input type="email" name="email" id="email"><br><br>
    昵称：<input type="text" name="nick_name"><br><br>
    密码：<input type="password" name="password"><br><br>
    重复密码：<input type="password" name="re_password"><br><br>
    <input type="submit">
</form>
```

> 后端和前端验证是必要的，因为前端验证可以有办法跳过。
>
> 注意<u>业务路由</u>（处理逻辑）和<u>UI路由</u>（展示页面）的区别。

##### # Router路由器

Router 是一个完整的中间件和路由系统，也可以看做是一个小型的app对象。

> 为了更好的分类管理route（类比于路由器和端口的概念）

<u>使用Router改注册登录页面案例</u>：

**UIRouter.js**：

```js
/*
* 专门用于管理展示界面的UI路由
* */

//引入Router构造函数
const {Router} = require('express')
//创建一个Router实例（路由器就是一个小型的app）
let router = new Router()
//引入path模块----Node中内置的一个专门用于解决路径问题的库
let {resolve} = require('path') // 解构赋值

router.get('/login',(req,res)=>{
    let url = resolve(__dirname,'../public/login.html')
    res.sendFile(url)
})

router.get('/register',(req,res)=>{
    let url = resolve(__dirname,'../public/register.html')
    res.sendFile(url)
})

module.exports = function () {
    return router
}
```

**loginRegisterRouter.js**：

```js
/*
* 专门用于管理登录、注册的业务路由
* */

//引入Router构造函数
const {Router} = require('express')
//创建一个Router实例（路由器就是一个小型的app）
let router = new Router()
//引入模型对象
let usersModel = require('../model/usersModel')

router.post('/register',(req,res)=>{
    // 此处省略
})

router.post('/login',(req,res)=>{
    // 此处省略
})

module.exports = function () {
    return router
}
```

**server.js**：

```js
const express = require('express')
const app = express()
//禁止服务器返回X-Powered-By,为了安全
app.disable('x-powered-by')
app.use(express.static(__dirname+'/public'))
const db = require('./db/db')
app.use(express.urlencoded({extended:true}))
//引入UI路由器
const UIRouter = require('./router/UIRouter')
//引入登录注册路由器
const loginRegisterRouter = require('./router/loginRegisterRouter')
db(()=>{
    //使用UIRouter
    app.use(UIRouter())
    //使用loginRegisterRouter
    app.use(loginRegisterRouter())

    app.listen(3000,(err)=>{
        if(!err) console.log('服务器启动成功！')
        else console.log(err)
    })
},(err)=>{
    console.log('数据库连接失败',err)
})
```

> **备注**：
>
> 1. 中间件本质是一个函数，所以在接口暴露的时候必须要暴露一个函数，然后在函数内部返回对象。
>
> 2. Node的内置path模块专门要来解决路径的问题。

### 三、EJS模板

#### 1. 概念

`EJS`是一个高效的 JavaScript 模板**后端**引擎。

> 简单来说，使用`EJS`模板引擎就能动态渲染数据。art-template是前端模板引擎。

#### 2. 安装与使用

下载：`npm i ejs -g`

基础使用：

**index.js**:

```js
const express = require('express')
const app = express()
//让你的服务器知道你在用哪一个模板引擎-----配置模板引擎
app.set('view engine','ejs')
//让你的服务器知道你的模板在哪个目录下，配置模板目录
app.set('views','./haha')

//如果在express中基于Node搭建的服务器，使用ejs无需引入。
app.get('/show',function (request,response) {
    let personArr = [
        {name:'peiqi',age:4},
        {name:'suxi',age:5},
        {name:'peideluo',age:6}
    ]
    response.render('person',{persons:personArr,a:1})
})

app.listen(3000,function (err) {
    if (!err) console.log('服务器启动成功了')
    else console.log(err)
})
```

**person.ejs**:

```ejs
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>show</title>
</head>
<body>
<%
for (var i=0; i<persons.length; i++ ){
    let item = persons[i] %>
<ul>
    <li class="name">姓名：<%=item.name%></li>
    <li>年龄：<%=item.age%></li>
</ul>
<%}%>
</body>
</html>
```

**`ejs`语法**：

- `< % % >`   里面能写任意js代码，但是不会向浏览器输出任何东西。
- `< %- % >`  能够将后端传递过来对象指定key所对应value渲染的页面
- `< %= % >`  能够将后端传递过来对象指定key所对应value不渲染的页面

> **备注**：这是前后端不分离的情况，就是前端语句和后端语句杂糅在一起了，非常不友好。日后趋势是前后端分离。

<u>使用`ejs`改注册登录页面案例</u>：（只以登录为例子）

**登录的业务路由**：

```js
router.post('/login',(req,res)=>{
    //1.获取输入
    const {email,password} = req.body
    //2.准备正则
    const emailReg = /^[a-zA-Z0-9_]{4,20}@[a-zA-Z0-9]{2,10}\.com$/
    const passwordReg = /^[a-zA-Z0-9_@#.+&]{6,20}$/
    //3.准备一个用于收集错误的对象
    const errMsg = {}
    if(!emailReg.test(email)){
        errMsg.emailErr = '邮箱格式不合法，用户名必须4-20位，主机名必须2-10位'
    }
    if(!passwordReg.test(password)){
        errMsg.passwordErr = '密码格式不合法，必须6-20'
    }
    // 使用JSON.stringify转译成字符串
    if(JSON.stringify(errMsg) !== '{}'){
        res.render('login',{errMsg})
        return
    }
    //3.去数据库中查找：
    usersModel.findOne({email,password},(err,data)=>{
        if(err){
            console.log(err)
            errMsg.networkErr = '网络不稳定，稍后重试'
            res.render('login',{errMsg})
            return
        }
        if(data){
            res.redirect('https://www.baidu.com')
            return
        }
        errMsg.loginErr = '用户名或密码输入错误！'
        res.render('login',{errMsg})
    })
})
```

> 备注：`JSON.stringify`可以将对象转译成JSON字符串

**login.ejs**：

```ejs
<body>
<span class="err"><%=errMsg.networkErr%></span>
<span class="err"><%=errMsg.loginErr%></span>
<form action="http://localhost:3000/login" method="post">
    邮箱：<input type="email" name="email" value="<%=errMsg.email%>"><span class="err"><%=errMsg.emailErr%></span><br><br>
    密码：<input type="password" name="password"><span class="err"><%=errMsg.passwordErr%></span><br><br>
    <input type="submit">
</form>
</body>
```

### 四、cookie

#### 1. 概念

本质就是一个**字符串**，里面包含着浏览器和服务器沟通的信息（交互时产生的信息）。

存储的形式以：**key-value**的形式存储。

浏览器会自动携带该网站的cookie，只要是该网站下的cookie，**全部携带**。

#### 2. 分类

**会话cookie**：关闭浏览器后，会话`cookie`会自动消失，会话`cookie`存储在浏览器运行的那块**内存**上。

**持久化cookie**：看过期时间，一旦到了过期时间，自动销毁，存储在用户的硬盘上,备注：如果没有到过期时间，同时用户清理了浏览器的缓存，持久化`cookie`也会消失。

#### 3. 工作原理

1. 当浏览器第一次请求服务器的时候，服务器可能返回一个或多个`cookie`给浏览器。

2. 浏览器判断`cookie`种类：
   会话`cookie`：存储在浏览器运行的那块内存上
   持久化`cookie`：存储在用户的硬盘上

3. 以后请求该网站的时候，自动携带上该网站的所有`cookie`（无法进行干预）

4. 服务器拿到之前自己“种”下`cookie`，分析里面的内容，校验`cookie`的合法性，根据`cookie`里保存的内容，进行具体的业务逻辑。

#### 4. 应用

解决http<u>无状态</u>的问题（例子：7天免登录，一般来说不会单独使用`cookie`，一般配合后台的`session`存储使用）

> 备注：`cookie`不一定只由服务器生成，前端同样可以生成`cookie`，但是前端生成的`cookie`几乎没有意义。

#### 5. 简单使用

```js
let express = require('express')
let cookieParser = require('cookie-parser')

let app = express()
app.use(cookieParser()) // 记得写

//demo路由不对cookie进行任何操作
app.get('/demo',function (req,res) {
    res.send('我是demo路由给你的反馈，我没有对cookie进行任何的操作')
})

//会话cookie，关闭浏览器即立刻消失
//demo1路由，负责给客户端“种”下一个会话cookie
app.get('/demo1',function (req,res) {
    //express中给客户端“种”cookie不需要任何的库
    let obj = {school:'atguigu',subject:'qianduan'}
    res.cookie('peiqi',JSON.stringify(obj)) //给客户端种下一个会话cookie
    res.send('我是demo1路由给你的反馈，我给你种下了一个【会话cookie】，你赶紧去浏览器里看看！')
})

//demo2路由，负责给客户端“种”下一个持久化cookie
app.get('/demo2',function (req,res) {
    let obj = {school:'atguigu2',subject:'qianduan2'}
    res.cookie('peiqi',JSON.stringify(obj),{maxAge:1000 * 60 * 60 *24 *30}) //给客户端种下一个持久化cookie
    res.send('我是demo2路由给你的反馈，我给你种下了一个【持久化cookie】，你赶紧去浏览器里看看！')
})

//demo3路由，负责读取客户端所携带过来的cookie
app.get('/demo3',function (req,res) {
    //express中读取客户端携带过来的cookie要借助一个中间件，名为：cookie-parser
    console.log(req.cookies);
    const {peiqi} = req.cookies
    let a = JSON.parse(peiqi)
    console.log(a.school)
    res.send('我是demo3路由,我读取了你携带过来的cookie，你去服务器控制台看看吧')
})

//demo4路由，负责告诉客户端删除一个cookie
app.get('/demo4',function (req,res) {
    //第一种方法：res.cookie('peiqi','',{maxAge:0})
    res.clearCookie('peiqi')
    res.send('兄台，我删除了你所保存的key为peiqi的那个cookie')
})

app.listen(3000,function (err) {
    if(err) console.log(err)
    else console.log('演示cokkie服务器启动成功了')
})
```

> 备注：`express`中读取客户端携带过来的`cookie`要借助一个中间件，名为：**`cookie-parser`**

<u>利用`cookie`完善登录和个人中心页面</u>：

**UI路由.js（部分）**：

```js
const cookieParser = require('cookie-parser')
router.use(cookieParser())
//用于展示个人中心界面的路由，无其他任何逻辑 ----- UI路由
router.get('/user_center',(req,res)=>{
    const {_id} = req.cookies
    if(_id){
        //去数据库中查找是否有此id
        //查到了--获取该id对应的昵称
        usersModel.findOne({_id},function (err,data) {
            if(!err && data){
                //进入此判断意味着：用户不仅携带了id，而且id有效
                res.render('userCenter',{nickName:data.nick_name})
            }else{
                //进入此处意味着：1.与数据库交互时产生了错误。2.用户非法篡改了cookie
                res.redirect('http://localhost:3000/login')
            }
        })
    }else{
        //进入此处意味着：1.用户的cookie过期了。2.用户清理了浏览器缓存。3.用户根本没有登录过，直接访问的个人中心。
        res.redirect('http://localhost:3000/login')
    }
})
```

**业务路由.js（部分）**：

```js
if(data){
    res.cookie('_id',data._id,{maxAge:1000*60})
    res.redirect(`http://localhost:3000/user_center`)
    return
}
```

### 五、session

#### 1. 概念

标准来说，session这个单词指的是会话。

前端通过浏览器去查看`cookie`的时候，会发现有些cookie的过期时间是：`session`，意味着该cookie是会话`cookie`。

后端人员常常把**session会话存储**简称为：`session`存储，或者更简单的称为：`session`

#### 2. 特点

存在于服务端；存储的是浏览器和服务器之间沟通产生的一些**信息**。

> 默认`session`的存储在服务器的**内存**中，每当一个新客户端发来请求，服务器都会新开辟出一块空间，供`session`会话存储使用。

#### 3. 工作流程

1. 第一次浏览器请求服务器的时候，服务器会开辟出一块内存空间，供`session`会话存储使用

2. 返回响应的时候，会自动返回一个`cookie`（有时候会返回多个，为了安全），`cookie`里包含着，上一步产生会话存储“容器”的**编号**（id）

3. 以后请求的时候，会自动携带这个`cookie`，给服务器

4. 服务器从该`cookie`中拿到对应的`session`的**id**，去服务器中匹配

5. 服务器会根据匹配信息，决定下一步逻辑

**注意**：

1. 一般来说`cookie`一定会配合`session`使用。
2. 服务端一般会做`session`的**持久化**，防止由于<u>服务器重启</u>，造成`session`的丢失。

> `session`什么时候销毁？
>
> - 服务器没有做`session`的持久化的同时，服务器重启了。
>
> *                  给客户端种下的那个用于保存`session`编号的`cookie`销毁了，随之服务器保存的session销毁(不管是否做了session的持久化)。
> *                  用户主动在网页上点击了“注销” “退出登录”等等按钮。

<u>用session完善登录和个人中心页面</u>：

**server.js（服务器部分）**：

```js
//如下代码是配置express中操作session
//引入express-session，用于在express中简化操作session
const session = require('express-session');
//引入connect-mongo，用于做session持久化
const MongoStore = require('connect-mongo')(session);

app.use(session({
    name: 'peiqi',   //返回给客户端cookie的key。
    secret: 'atguigu', //参与加密的字符串（又称签名）
    saveUninitialized: false, //是否在存储内容之前创建session会话
    resave: true ,//是否在每次请求时，强制重新保存session，即使他们没有变化（比较保险）
    store: new MongoStore({
        url: 'mongodb://localhost:27017/sessions_container',
        touchAfter: 24 * 3600 //修改频率（例：//在24小时之内只更新一次）
    }),
    cookie: {
        httpOnly: true, // 开启后前端无法通过 JS 操作cookie
        maxAge: 1000*30 // 设置cookie的过期时间,cookie的key，cookie的value，均不在此处配置。
    },
}));
```

**业务逻辑部分.js**：

```js
router.post('/login',(req,res)=>{
    // ...
    usersModel.findOne({email,password},(err,data)=>{
        if(err){
            // ...
        }
        if(data){
            //1.为请求开辟一个session会话存储空间
            //2.将客户端与服务器沟通产生的数据放入session会话存储空间
            //3.获取session会话存储空间的id
            //4.返回给客户端一个cookie，包含着：将上一步的id。
            req.session._id = data._id.toString()
            res.redirect(`http://localhost:3000/user_center`) 
            return
        }
        // ...
    })

})

```

**UI逻辑部分.js**：

```js
router.get('/user_center',(req,res)=>{
    //1.获取客户端通过cookie携带过来的session编号
    //2.根据session编号匹配session容器
    //3.若匹配上：拿到session容器里的数据，去使用
    //4.若未匹配上：驳回，去登录
    const {_id} = req.session // req携带过来的是cookie：{key:peiqi,value:经过加密的session编号}
    if(_id){
        // ....
    }else{
        // ...
    }
})
```

> 备注：为了操作`session`并且持久化，需要两个中间件。**`express-session`**和**`connect-mongo`**。
>
> 小知识📌：很多主流网站只要将你的个人页面cookie全部导出，就可以用这个cookie来登录网站。但只要有一方退出，服务器session就会消失。

#### 4. 数据加密

为了安全性要对数据库的重要信息进行加密，比如用户注册时的密码。

目前常用的数据加密技术有`md5`和`sha1`。（`sha1`比`md5`略强）

##### # md5

**安装**：`npm i md5 -g`

**使用**：

```js
// 引入md5加密模块
let md5 = require('md5')
// 注册
usersModel.create({email,nick_name,password:md5(password)},function (err) {
    // ...
})
// 登录
usersModel.findOne({email,password:md5(password)},(err,data)=>{
    // ...
})
```

##### # sha1

**安装**：`npm i sha1 -g`

**使用**：

```js
// 引入sha1 加密模块
let md5 = require('sha1 ')
// 注册
usersModel.create({email,nick_name,password:sha1 (password)},function (err) {
    // ...
})
// 登录
usersModel.findOne({email,password:sha1 (password)},(err,data)=>{
    // ...
})
```



















