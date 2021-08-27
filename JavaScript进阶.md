## PC 端网页特效

### 元素偏移量 offset 系列

#### offset 概述

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

#### offset 与 style 区别

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

### 元素可视区 client 系列

client 翻译过来就是客户端，我们使用 client 系列的相关属性来获取元素可视区的相关信息。

> 和offset的区别在于不包含边框。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/0d1be4fe84288d89f9972a4d08108af9.jpg" alt="0d1be4fe84288d89f9972a4d08108af9.jpg" border="0" />

### 元素滚动 scroll 系列

#### 元素 scroll 系列属性

scroll 翻译过来就是滚动的，我们使用 scroll 系列的相关属性可以动态的得到该元素的大小、滚动距离等。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/b3cee4541278141c05edd618127022b4.jpg" alt="b3cee4541278141c05edd618127022b4.jpg" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/06/21/8878c1836a4b5113e65bce4980b82915.jpg" alt="8878c1836a4b5113e65bce4980b82915.jpg" border="0" />

#### 页面被卷去的头部

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

### 动画函数封装

#### 动画实现原理

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

#### 动画函数简单封装

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

#### 给不同元素记录不同定时器

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

#### 缓动效果原理

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

#### 多个目标值之间移动

可以让动画函数从 800 移动到 500。 当我们点击按钮时候，判断步长是正值还是负值。

```js
var step = (target - obj.offsetLeft) / 10;
step = step > 0 ? Math.ceil(step) : Math.floor(step);
```

#### 动画函数添加回调函数

**回调函数原理**：函数可以作为一个**参数**。将这个函数作为参数传到另一个函数里面，当那个函数执行完之后， 再执行传进去的这个函数，这个过程就叫做**回调**。

> 回调函数写的位置：定时器结束的位置。

```js
animate(span, 800, function() {
    // alert('你好吗');
    span.style.backgroundColor = 'red';
});
```

#### 封装到单独JS文件里面

因为以后经常使用这个动画函数，可以单独封装到一个JS文件里面，使用的时候引用这个JS文件即可。

### 常见网页特效案例

#### 网页轮播图

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

#### 返回顶部

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

#### 筋头云案例

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

## 移动端网页特效

### 触屏事件

#### 概述

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

#### 触摸事件对象（TouchEvent）

TouchEvent 是一类描述手指在触摸平面（触摸屏、触摸板等）的状态变化的事件。

touchstart、touchmove、touchend 三个事件都会各自有事件对象。

触摸事件对象重点我们看三个常见对象列表：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/22/5103586df7f1cd7027c52613001520af.jpg" alt="5103586df7f1cd7027c52613001520af.jpg" border="0" />

> 因为平时我们都是给元素注册触摸事件，所以重点记住 targetTouches

#### 移动端拖动元素

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

### 移动端常见特效

#### 移动端轮播图

[建议自己做一下。]([JavaScript基础语法-dom-bom-js-es6新语法-jQuery-数据可视化echarts黑马pink老师前端入门基础视频教程(500多集)持续_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Sy4y1C7ha?p=340&spm_id_from=pageDriver))

> 配合CSS3使用更好。另外手指可以滑动图片。

#### classList 属性

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

### 移动端常用开发插件

#### 什么是插件

JS 插件是 **js 文件**，它遵循一定规范编写，方便程序展示效果，拥有特定功能且方便调用。如轮播图和瀑布流插件。

> 特点：它一般是为了解决某个问题而专门存在，其功能单一，并且比较小。

#### 插件的使用

引入 js 插件文件、按照规定语法使用。

#### Swiper 插件的使用

中文官网地址： https://www.swiper.com.cn/ 

#### 其他移动端常见插件

superslide： http://www.superslide2.com/

iscroll： https://github.com/cubiq/iscrol

### 移动端常用开发框架

#### 框架概述

**框架**，顾名思义就是一套架构，它会基于自身的特点向用户提供一套较为完整的解决方案。框架的控制权在框架本身，使用者要按照框架所规定的某种规范进行开发。

**插件**一般是为了解决某个问题而专门存在，其功能单一，并且比较小。

前端常用的框架有 **Bootstrap**、**Vue**、Angular、**React** 等。既能开发PC端，也能开发移动端

前端常用的移动端插件有 swiper、superslide、iscroll等。 插件一般是为了解决某个问题而专门存在，其功能单一，并且比较小。

> 框架： 大而全，一整套解决方案
>
> 插件： 小而专一，某个功能的解决方

#### Bootstrap

Bootstrap JS插件**使用步骤**：

1. 引入相关js 文件
2. 复制HTML 结构
3. 修改对应样式
4. 修改相应JS 参数

## 本地存储

随着互联网的快速发展，基于网页的应用越来越普遍，同时也变的越来越复杂，为了满足各种各样的需求，会经常性<u>在本地存储大量的数据</u>，HTML5规范提出了相关解决方案。

### 本地存储特性

1、数据存储在用户**浏览器**中

2、设置、读取方便、甚至页面刷新**不丢失**数据

3、容量较大，sessionStorage约5M、localStorage约20M

4、只能存储**字符串**，可以将对象JSON.stringify() 编码后存储

### sessionStorage

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

### localStorage

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

















