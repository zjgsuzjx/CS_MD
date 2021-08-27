> 💥此MD/PDF/HTML文档由 [@竹梦者也 ](https://www.zjgsuzjx.top/)编辑制作，不可贩卖❌。仅供学习交流使用，下载后切勿随意传播。转载麻烦加上出处~
>
> 📌欢迎在留言区提供修改建议~
>
> 💌本文内容和代码来自于`tianyu`老师的`webpack`教程
>
> ✨本笔记所有相关配置已兼容**webpack-5.38.1**版本，请根据你的版本`webpack -v`正确食用。
>
> 
>
> ✅2021.7.13	 @竹梦者也(https://www.zjgsuzjx.top) 
>







## 一、webpack4.0

### 一、基本概念

#### 1. 铺垫

`grunt`->`gulp`->`webpack`（**主流**）

**源代码**：程序员写的没有经过任何的加工的代码
源代码最好经过层层的加工处理

`src`----源代码---程序员写的没有经过任何的加工的代码--------生的鸡蛋、生的大米。

`dist/build/built`----加工之后的代码---经过层层的加工处理的代码----------蛋炒饭

**构建**：将程序写的源代码，经过编译、压缩、语法检查、兼容性处理、生成浏览器可以高效、稳定运行的代码

#### 2. 含义

* `Webpack`是一个模块打包器(`bundler`)。
* 在`Webpack`看来, 前端的所有资源文件(`js`/`json`/`css`/`img`/`less`/...)都会作为模块处理
* 它将根据模块的依赖关系进行静态分析，生成对应的静态资源

#### 3. 核心概念

* `Entry`：入口起点(entry point)指示 `webpack` 应该使用哪个模块，来作为构建其内部依赖图的开始。
* `Output：output` 属性告诉 `webpack` 在哪里输出它所创建的 bundles，以及如何命名这些文件，默认值为 `./dist`。
* `Loader`：`loader` 让 `webpack` 能够去处理那些非 `JavaScript` 文件（`webpack` 自身只能解析 JavaScript）。
* `Plugins`：插件则可以用于执行范围更广的任务。插件的范围包括，从打包优化和压缩，一直到重新定义环境中的变量等。
* `Mode`：模式，有生产模式production和开发模式development

#### 4. 理解Loader

* `Webpack` 本身只能加载JS/JSON模块，如果要加载其他类型的文件(模块)，就需要使用对应的`loader` 进行转换/加载
* `Loader` 本身也是运行在 node.js 环境中的 JavaScript 模块
* 它本身是一个函数，接受源文件作为参数，返回转换的结果
* `loader` 一般以 `xxx-loader` 的方式命名，xxx 代表了这个 `loader` 要做的转换功能，比如 `json-loader`。

#### 5. 理解Plugins

* 插件可以完成一些`loader`不能完成的功能。
* 插件的使用一般是在 `webpack` 的配置信息 `plugins` 选项中指定。

### 二、简单使用过程

#### 1. 安装

* `npm i webpack webpack-cli -g`  //全局安装,作为指令使用
* `npm i webpack webpack-cli -D` //本地安装,作为本地依赖使用

#### 2. 项目初始化

生成`package.json`文件

如：

```json
{
  "name": "webpack_test",
  "version": "1.0.0"
}
```

#### 3. 原生打包JS和JSON

**举例**

**创建`js`文件**：

* `src/js/index.js`

```js
/*
注意！！！
该index.js不同于学习链块化时，那个用于汇总js的文件。
模块化技术的index.js只用于汇总各个js模块。
该index.js 是webpack的【入口文件】
该文件可以用于汇总：js、css、图片、音频、视频
*/
import {sum} from './module1'
import {sub} from './module2'
import module3 from './module3'
import a from '../json/test.json'

console.log(sum(1, 2))
console.log(sub(3, 4))
console.log(module3.mul(5, 6))
console.log(module3.div(10, 5))

console.log(a, typeof a)

// webpack只管翻译es6的模块化语法变为浏览器认识的，但是不会处理其他语法
setTimeout(() => {
    console.log('hello')
}, 1000)
```

* `src/js/module1.js`
* `src/js/module2.js`
* `src/js/module3.js`

**创建`json`文件**：

- `src/json/test.json`  

**创建主页面**: 

- `src/index.html`

**运行指令**：

* 开发配置指令：`webpack ./src/js/index.js -o dist/js --mode development`
  * 功能: `webpack`能够编译打包`js`和`json`文件，并且能将es6的模块化语法转换成浏览器能识别的语法
* 生产配置指令：`webpack ./src/js/index.js -o dist/js --mode production`
  * 功能: 在开发配置功能上加上一个**压缩**代码

> 注意：我是**webpack5.38.1**， 与4的区别是必须要求目录前面加上 `./`，且默认文件名为`main.js`

<img src="https://img.zjgsuzjx.top/img/images/2021/07/12/c4a064265825adaa315a6e39c70575d4.jpg" alt="c4a064265825adaa315a6e39c70575d4.jpg" border="0" />

**结论**：

* `webpack`能够编译打包`js`和`json`文件
* 能将es6的模块化语法转换成浏览器能识别的语法
* 能压缩代码

**缺点**：

* 不能编译打包`css`、`img`等文件
* 不能将`js`的es6基本语法转化为es5以下语法

**改善**：

使用`webpack`配置文件解决，自定义功能

### 三、使用webpack配置文件

官方中文文档：https://webpack.docschina.org/concepts/

**目的**：在项目根目录定义配置文件，通过自定义配置文件，还原以上功能

**文件名称**：`webpack.config.js`

**文件内容**：

```js
const {resolve} = require('path'); //node内置核心模块，用来设置路径。
module.exports = {
    entry: './src/js/index.js',   // 入口文件配置（简写）
    /*完整写法：
      entry:{
        main:'./src/js/app.js'
      }
    */
    output: {                     // 输出配置
        filename: './js/index.js',      // 输出文件名
        path: resolve(__dirname, 'build')   //输出文件路径配置
    },
    // mode: 'development'   //开发环境(二选一)
    mode: 'production'   //生产环境(二选一)
};
```

**运行指令**： `webpack`

### 四、使用工具

#### 1. 打包less资源

**概述**：less文件webpack不能解析，需要借助loader编译解析

**创建less文件**：

* `src/less/test1.less`
* `src/less/test2.less`

**在index.js文件引入**：

```js
import '../less/test.less'
```

**安装loader**：

`npm install css-loader style-loader less-loader less -D`

**配置loader**：

```js
module: {
    // 所有的loader都要再module对象中的rules属性中
    // rules是一个数组，数组中的每一个对象就是一个loader
    rules: [
        {
            test: /\.less$/i, // 匹配所有的less文件
            use: [
                // 使用lessloader，将less编译为CSS
                'style-loader',
                'css-loader',
                'less-loader',
            ],
        },
    ],
}
```

> 注意：上端代码加在`module.exports`里。

**运行指令**：`webpack`

#### 2. JS语法检查

**概述**：对`js`基本语法错误/隐患，进行提前检查

**安装loader**：`npm install eslint-loader eslint -D`

> 注意：现在已经被弃用了
>
> 在：eslint.org网站 -> userGuide -> Configuring ESLint 查看如何配置
>
> 在：eslint.org网站 -> userGuide -> Rules 查看所有规则
>
> 官方中文文档：https://cn.eslint.org/

**配置loader**：

```js
{
    test: /\.js$/,  //只检测js文件
    exclude: /node_modules/,  //排除node_modules文件夹
    enforce: "pre",  //提前加载使用
    use: { //使用eslint-loader解析
        loader: "eslint-loader"
    }
}
```

> 需要加在`module`的`rules`里。

**修改package.json**：

```json
"eslintConfig": {
  "parserOptions": {
    "ecmaVersion": 6, 
    "sourceType": "module"
  },
  "env": { // 设置环境
    "browser": true,   // 支持浏览器环境： 能够使用window上的全局变量
    "node": true,       // 支持服务器环境:  能够使用node上global的全局变量
      "es6": true // 支持es6新语法
  },
  "globals": { // 声明使用的全局变量, 这样即使没有定义也不会报错了
    "$": "readonly"    // $ 只读变量
  },
  "rules": {  // eslint检查的规则  0 忽略 1 警告 2 错误
    "no-console": 0,   // 不检查console
    "eqeqeq": 2,   // 用==而不用===就报错
    "no-alert": 2 // 不能使用alert
  },
  "extends": "eslint:recommended" // 使用eslint推荐的默认规则 https://cn.eslint.org/docs/rules/
}
```

> 注意：JSON不能有注释！记得删掉

**运行指令**：`webpack`

#### 3. JS语法转换

**概述**：将浏览器不能识别的新语法转换成原来识别的旧语法，做浏览器兼容性处理

**安装loader**：`npm install babel-loader @babel/core @babel/preset-env --save-dev`

**配置loader**：

```js
{
    test: /\.js$/,
    exclude: /node_modules/,
    use: {
        loader: "babel-loader",
        options: {
            presets: ['@babel/preset-env']
        }
    }
}
```

> 要加在`module`的`rules`里。

**运行指令**：webpack

> **缺点**：不能转换高级语法比如Promise，也不能兼容IE旧版本浏览器。

#### 4. JS兼容性处理

##### # 第一种方法

使用经典的`polyfill`

**安装**：`npm install @babel/polyfill`

**使用**：

在`index.js`（入口JS文件）加入下面代码，最好放在最上面

```js
import '@babel/polyfill'; // 包含ES6的高级语法的转换
```

**优点**：解决`babel`只能转换部分低级语法的问题(如：`let`/`const`/解构赋值...)，引入`polyfill`可以转换高级语法(如:`Promise`)

**缺点**：将所有高级语法都进行了转换，但实际上可能只使用一部分。所以<u>导致文件变得很大很大</u>。

**解决**：需要按需加载（使用了什么高级语法，就转换什么，而其他的不转换）

##### # 第二种方法

借助按需引入`core-js`按需引入。

**安装**：`npm install core-js`

**配置loader**：

```js
// js语法转换（es6->es5）
{
    test: /\.js$/,
    exclude: /(node_modules)/,
    use: {
        loader: 'babel-loader',
        options: {
            presets: [
                [
                    '@babel/preset-env',
                    {
                        useBuiltIns: 'usage',  // 按需引入需要使用polyfill
                        corejs: {version: 3}, // 解决不能找到core-js的问题
                        targets: { // 指定兼容性处理哪些浏览器
                            "chrome": "58",
                            "ie": "9",
                        }
                    }
                ]
            ],
            cacheDirectory: true, // 开启babel缓存
        }
    }
}
```

> 要加在`module`的`rules`里。
>
> 补充：将浏览器兼容性版本调高可以减小压缩后的文件大小。

#### 5. 打包样式文件中的图片资源

**概述**：图片文件webpack不能解析，需要借助loader编译解析

**添加2张图片**:

* 小图, 小于8kb: `src/images/vue.png`
* 大图, 大于8kb: `src/images/react.jpg`

> Base64编码适合于8kb以下图片。

**引入图片**：在less或css文件中通过背景图的方式引入图片

**安装loader**：

`npm install file-loader url-loader -D` 

> 补充：`url-loader`是对象`file-loader`的上层封装，使用时需配合`file-loader`使用。

**配置loader**：

```js
{
    test: /\.(png|jpg|gif)$/,
    use: {
        loader: 'url-loader',
        options: {
            limit: 8192, // 8kb --> 8kb以下的图片会base64处理
            outputPath: 'images', // 决定文件本地输出路径
            publicPath: '../build/images',  // 决定图片的url路径
            name: '[hash:8].[ext]' // 修改文件名称 [hash:8] hash值取8位  [ext] 文件扩展名
        }
    }
}
```

**运行指令**：`webpack`

#### 6. 打包html文件

**概述**：`html`文件`webpack`不能解析，需要借助**插件**编译解析

**添加html文件**：`src/index.html`

> 注意不要在html中引入任何css和js文件

**安装插件**：

`npm install html-webpack-plugin -D`

**配置Plugins**：

在`webpack.config.js`中引入插件（插件都需要手动引入，而`loader`会自动加载）

```js
const HtmlWebpackPlugin = require('html-webpack-plugin')
```

以下代码与`module`平行关系：

```js
// 配置插件
plugins: [
    new HtmlWebpackPlugin({
        template: './src/index.html', // 以当前文件为模板创建新的HtML(1. 结构和原来一样 2. 会自动引入打包的资源)
    }),
]
```

**运行指令**：`webpack`

#### 7. 打包html中图片资源

**概述**：`html`中的图片`url-loader`没法处理，它只能处理`js`中引入的图片 / 样式中图片，不能处理`html`中`img`标签，需要引入其他`html-loader`处理。

**添加图片**：在`src/index.html`添加两个`img`标签

**安装loader**：

`npm install html-loader -D` 

**配置loader**：

```js
{
    test: /\.(html)$/,
        use: [
            {
                loader: 'html-loader',
                options: {
                    // 不使用es模块，防止图片地址错误
                    esModule: false 
                }
            }
        ]
}
```

#### 8. 打包媒体资源

**概述**：其他资源`webpack`不能解析，需要借助`loader`编译解析

**添加字体文件（举例）**：`src/media/iconfont.ttf`（以阿里图标为例）

**修改样式**：

```less
@font-face {
  font-family: "iconfont"; /* Project id  */
    // 统一把字体图标放到media下面
  src: url('../media/iconfont.ttf?t=1626110174654') format('truetype');
}

.iconfont {
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.icon-cangchucangku:before {
  content: "\e98c";
}

.icon-bingtutubiao:before {
  content: "\e98d";
}

.icon-chayan:before {
  content: "\e98e";
}
```

**在index.js引入**：

```js
import '../css/iconfont.less'
```

**html里添加字体**：

```html
<span class="iconfont icon-bingtutubiao"></span>
```

**配置loader**：

```js
{
    test: /\.(eot|svg|woff|woff2|ttf|mp3|mp4|avi)$/,  // 处理其他资源
    loader: 'file-loader',
    options: {
        outputPath: 'media',
        name: '[hash:8].[ext]'
    }
}
```

**运行指令**：`webpack`

#### 9. 自动编译打包运行

**概念**：能够将所有打包后的文件放在内存里，并且自动配置并打开了一个服务器，能够实现实时刷新页面。不会在本地输出文件。

> 详细配置见官网：指南 -> 开发环境 -> 使用webpack-dev-server 
>
> 自动刷新：live-reload 是webpack-dev-server 自带的

**安装loader**：

`npm install webpack-dev-server -D`

**配置对象**：

```js
// 配置自动化编译
devServer: {
    open:true, // 自动打开浏览器
    compress:true, // 启动gzip压缩
    port:3000 // 端口号
}
```

> 注意这段代码和`module`是平行关系。
>

**修改url-loader部分配置**：

```js
loader: 'url-loader',
options: {
    limit: 8192, 
    outputPath: 'images', 
    publicPath: 'images/',  // 修改文件途径，因为构建工具以build为根目录，不用再找build了
    name: '[hash:8].[ext]' 
}
```

**修改package.json**：

```js
"scripts": {
    "start": "webpack serve"
 }
```

**运行指令**：`npm start` 

> 注意：`webpack-dev-server`指令才能启动`devServer`配置，然后配置到`package.json`中才行
>

#### 10. 热模替换功能

**概述**：热模块替换（`HMR`）是webpack提供的最有用的功能之一。它允许在运行时更新所有类型的模块，而无需完全刷新（<u>只更新</u><u>变化的模块</u>，不变的模块不更新）。

> 详细配置见官网：指南 -> 模块热替换
>

**修改devServer配置**：

```js
devServer: {
    open:true, 
    compress:true, 
    port:3000, 
    hot:true // 开启热模替换功能 HMR
}
```

**问题**：`html`文件无法自动更新了，需要增加一个入口

```js
entry: ['./src/js/index.js','./src/index.html']
```

#### 11. devtool

**概述**： 一种将压缩/编译文件中的代码映射回源文件中的原始位置的技术，让我们调试代码不在困难

> 简单来讲就是出现错误时将定位到源代码的行号，而不是打包后的行号。
>
> 详细配置见官网：配置 -> devtool

**介绍**：

* cheap 只保留行, 编译速度快
* eval webpack生成的代码（每个模块彼此分开，并使用模块名称进行注释）, 编译速度快
* inline 以base64方式将source-map嵌入到代码中，缺点造成编译后代码体积很大

**推荐使用**：

```js
devtool: 'eval-cheap-module-source-map' // 开发环境
```

```js
devtool: 'cheap-module-source-map' // 生产环境
```

#### 12. 准备生产环境

**概念**：之前都是基于开发环境下的调试。在项目上线后就是生产环境了，所以会有较大的区别，需要单独为生产环境配置。

**第一步**：

创建文件夹`config`，将`webpack.config.js`复制两份。

* `./config/webpack.dev.js`
* `./config/webpack.prod.js`

之后<u>可以删除根目录下</u>的`webpack.config.js`。

**第二步**：

修改`webpack.prod.js`配置，删除`webpack-dev-server`配置。

修改`output`：

```js
output: {
    filename: './js/index.js',
    path: resolve(__dirname, '../build'), // 路径要翻出去
    publicPath: '/'  // 所有输出资源在引入时的公共路径，若loader中也指定了publicPath，会以loader的为准。
}
```

修改`mode`：

```js
mode: 'production'
```

修改`module`中的`url-loader`：

```js
{
    test: /\.(png|jpg|gif)$/,
    use: {
        loader: 'url-loader',
        options: {
            limit: 8192, 
            outputPath: 'images', 
            publicPath: '/images/',  // 重写publicPath，需要在路径前面加上 /
            name: '[hash:8].[ext]' 
        }
    }
}
```

修改`devtool`：

```js
devtool: 'cheap-module-source-map'
```

**第三步**：

修改`package.json`的脚本指令。

```js
"scripts": {
  "start": "webpack serve --config ./config/webpack.dev.js",
  "dev": "webpack server --config ./config/webpack.dev.js",
  "build": "webpack --config ./config/webpack.prod.js"
}
```

> 备注：`start`和`dev`的功能是一样的，部分企业会用后者。

**第四步**：

根据不同环境执行不同的指令。

- 开发环境指令

`npm start` 或 `npm run dev`

- 生产环境指令

`npm run build`

**第五步**：

> 注意: 生产环境代码需要部署到服务器上才能运行 （serve这个库能帮助我们快速搭建一个静态资源服务器）

安装：`npm i serve -g`  

执行：`serve -s build -p 5000`

#### 13. 清除打包文件目录

**概述**：每次打包生成了文件，都需要手动删除，引入插件帮助我们自动删除上一次的文件

**安装插件**：

`npm install clean-webpack-plugin -D`

**引入插件**：

```js
const { CleanWebpackPlugin } = require('clean-webpack-plugin'); // 注意要解构赋值！！！
```

> 上面代码放在`webpack.prod.js`最上方的引入部分

**配置插件**：

```js
plugins: [
    // ...
    new CleanWebpackPlugin()
]
```

**运行指令**：`npm run build`

#### 14. 提取css成单独文件

**安装插件**：

`npm install mini-css-extract-plugin -D`

**引入插件**：

```js
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
```

> 上面代码放在`webpack.prod.js`最上方的引入部分

**配置loader**：

```js
{
    test: /\.less$/i, // 匹配所有的less文件
    use: [
        MiniCssExtractPlugin.loader, // 将原来的替换掉
        'css-loader',
        'less-loader',
    ],
}
```

**配置插件**：

```js
new MiniCssExtractPlugin({
    filename: "css/[name].css",
})
```

**运行指令**：

`npm run build`

> **注意**：记住直接打开`build`里的`index.html`会报错，因为路径问题。所以要利用`serve -s build -p 5000`来打开

#### 15. 添加css兼容

> 不兼容5.0+，暂时找不到解决方法。

#### 16. 压缩css

**安装插件**：

`npm install optimize-css-assets-webpack-plugin -D`

**引入插件**：

```js
const OptimizeCssAssetsPlugin = require('optimize-css-assets-webpack-plugin');
```

**配置插件**：

```js
new OptimizeCssAssetsPlugin({
    cssProcessorPluginOptions: {
        preset: ['default', { discardComments: { removeAll: true } }],
    },
    cssProcessorOptions: { // 解决没有source map问题
        map: {
            inline: false,
            annotation: true,
        }
    }
}),
```

**运行指令**：`npm run build`

#### 17. 压缩html

**修改插件配置**：

```js
new HtmlWebpackPlugin({
    template: './src/index.html',
    minify: {
        removeComments: true, // 移除注释
        collapseWhitespace: true, // 折叠所有空白
        removeRedundantAttributes: true, // 移除无用的标签
        useShortDoctype: true, // 使用短的文档声明
        removeEmptyAttributes: true, // 移除空标签
        removeStyleLinkTypeAttributes: true, // 移除rel="stylesheet"
        keepClosingSlash: true, // 自结束
        minifyJS: true,
        minifyCSS: true,
        minifyURLs: true,
    }
})
```

**运行指令**：`npm run build`

### 五、总结

> 开发使用`start`，产品上线测试使用`build`和`serve`。

## 二、webpack5.0新特性

### 后续会更新

















