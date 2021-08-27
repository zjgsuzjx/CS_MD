> 💥此MD/PDF/HTML文档由 [@竹梦者也]([竹梦者也 - ZJXのBLOG (zjgsuzjx.top)](https://www.zjgsuzjx.top/)) 编辑制作，不可贩卖❌。仅供学习交流使用，下载后切勿随意传播。转载麻烦加上出处~
>
> 📌欢迎在留言区提供修改建议~
>
> 💌本文内容和代码来自于Pink老师的JS高级视频教程，有部分是ES6的新概念。
>
> 
>
> ✅2021.6.22	 @竹梦者也(https://www.zjgsuzjx.top) 





## 一、JavaScript 面向对象

### 一、面向对象编程介绍

#### 两大编程思想

- 面向过程
- 面向对象

### 二、面向过程编程 POP

**面向过程**(`Process-oriented programming`)就是分析出解决问题所需要的步骤，然后用函数把这些步骤一步一步实现，使用的时候再一个一个的依次调用就可以了。

> 面向过程，就是按照我们分析好了的步骤，按照步骤解决问题。

#### 1. 面向对象编程 OOP

**面向对象**(`Object Oriented Programming`)是把事务分解成为一个个对象，然后由对象之间分工与合作。

> 面向对象是以对象功能来划分问题，而不是步骤。

在面向对象程序开发思想中，每一个对象都是功能中心，具有明确分工。

面向对象编程具有灵活、代码可复用、容易维护和开发的优点，更适合多人合作的大型软件项目。

面向对象的特性：

- 封装性
- 继承性
- 多态性

#### 2. 面向过程和面向对象的对比

**面向过程**：

**优点**：性能比面向对象高，适合跟硬件联系很紧密 的东西，例如单片机就采用的面向过程编程。

**缺点**：没有面向对象易维护、易复用、易扩展

**面向对象**：

**优点**：易维护、易复用、易扩展，由于面向对象有 封装、继承、多态性的特性，可以设计出低耦合的 系统，使系统 更加灵活、更加易于维护

**缺点**：性能比面向过程低

> 小项目用面向过程，大项目用面向对象

### 三、ES6 中的类和对象

面向对象的**思维特点**: 

1. 抽取（抽象）对象共用的属性和行为组织(封装)成一个**类**(模板)
2. 对类进行**实例化**, 获取类的对象

#### 1. 对象

在 JavaScript 中，对象是一组无序的相关属性和方法的集合，所有的事物都是对象，例如字符串、数值、数组、 函数等。

#### 2. 类 class

在 ES6 中新增加了类的概念，可以使用 `class` 关键字声明一个类，之后以这个类来实例化对象。

#### 3. 创建类

**语法**：

```js
class star{
// ...
}
var xx = new star();
```

> 注意： 类必须使用 `new` 实例化对象

#### 4. 类 constructor 构造函数

`constructor()` 方法是类的构造函数(默认方法)，用于传递参数，返回实例对象，通过 `new` 命令生成对象实例时 ，自动调用该方法。如果没有显示定义, 类内部会自动给我们创建一个`constructor()` 。

```js
class star {
    constructor(uname) {
        this.uname = uname;
    }
}

var ldh = new star('zjgsuzjx');
console.log(ldh.uname);
```

> `constructor`会自动执行

#### 5. 类添加方法

```js
class star {
    constructor(uname) {
        this.uname = uname;
    }

    sing() {
        console.log(this.uname + "zjgsuzjx");
    }
}

var ldh = new star('zjgsuzjx');
ldh.sing();
```

> 我们类里面所有的函数不需要写`function`；多个函数方法之间不需要添加**逗号**分隔

### 四、类的继承

#### 1. 继承

程序中的继承：子类可以继承父类的一些属性和方法。使用 `extends` 关键字。

```js
class Father {
    constructor(surname) {
        this.surname= surname;
    }
    say() {
        console.log('你的姓是' + this.surname);
    }
}
class Son extends Father{ // 这样子类就继承了父类的属性和方法
}
var damao= new Son('刘');
damao.say();
```

> 注意，如果在子类重新声明构造函数，那父类的`this`不能调用新的构造函数里的变量，只能用`super`关键字解决。

#### 2. super 关键字

`super` 关键字用于访问和调用对象父类上的函数。可以<u>调用父类的构造函数</u>，也可以调用父类的普通函数。

```js
class Person { // 父类
    constructor(surname){
        this.surname = surname;
    }
}
class Student extends Person { // 子类继承父类
    constructor(surname,firstname){
        super(surname); // 调用父类的constructor(surname)
        this.firstname = firstname; // 定义子类独有的属性
    }
}
```

> 注意: 子类在构造函数中使用`super`, 必须放到 `this` 前面 (必须先调用父类的构造方法,在使用子类构造方法)

```js
class Father {
    say() {
        return '我是爸爸';
    }
}
class Son extends Father { // 这样子类就继承了父类的属性和方法
    say() {
        // super.say() super 调用父类的方法
        return super.say() + '的儿子';
    }
}
var damao = new Son();
console.log(damao.say());
```

```js
class fu {
    constructor(a, b) {
        this.a = a;
        this.b = b;
    }

    jiafa() {
        return this.a + this.b;
    }
}
class zi extends fu {
    constructor(a, b) {
        super();
    }

    jianfa() {
        return this.a - this.b;
    }
}

let z = new zi(1, 3);
console.log(z.jianfa()); // NaN
```

> 以上代码说明子类的`this`只会使用子类的`constructor`中定义的变量。

**三个注意点**：

1. 在 ES6 中类没有变量提升，所以必须先定义类，才能通过类实例化对象.
2. 类里面的共有属性和方法一定要加`this`使用. 
3. 类里面的`this`指向问题. 
4. `constructor` 里面的this指向**实例对象**, 方法里面的`this` 指向这个**方法的调用者**

```js
var that;
var _that;
class Star {
    constructor(uname, age) {
        // constructor 里面的this 指向的是 创建的实例对象
        that = this;
        console.log(this);
        this.uname = uname;
        this.age = age;
        // this.sing();
        this.btn = document.querySelector('button');
        this.btn.onclick = this.sing; // 不能加括号，不然网页打开后马上调用了
    }
    sing() {
        // 这个sing方法里面的this 指向的是 btn 这个按钮,因为这个按钮调用了这个函数
        console.log(this);
        console.log(that.uname); // that里面存储的是constructor里面的this
    }
    dance() {
        // 这个dance里面的this 指向的是实例对象 ldh 因为ldh 调用了这个函数
        _that = this;
        console.log(this);

    }
}

var ldh = new Star('刘德华');
console.log(that === ldh); // true
ldh.dance();
console.log(_that === ldh); // true
```

**面向对象版 tab 栏切换案例**

[视频地址](https://www.bilibili.com/video/BV1Kt411w7MP?p=17&spm_id_from=pageDriver)

**功能需求**:

- 点击 tab栏,可以切换效果. 
- 点击 + 号, 可以添加 tab 项和内容项.
- 点击 x 号, 可以删除当前的tab项和内容项.
- 双击tab项文字或者内容项文字,可以修改里面的文字内容.

**函数补充**：

利用 `insertAdjacentHTML`() 可以直接把字符串格式元素添加到**父元素**中。

`insertAdjacentHTML`(追加的位置,‘要追加的字符串元素’) ；追加的位置有: `beforeend` 插入元素内部的最后一个子节点**之后**

## 二、构造函数和原型

### 一、构造函数和原型

#### 1. 概述

在典型的 `OOP` 的语言中（如 `Java`），都存在类的概念，类就是对象的模板，对象就是类的实例，但在 `ES6`之前， `JS` 中并没用引入类的概念。

在 `ES6`之前 ，对象不是基于类创建的，而是用一种称为**构建函数**的特殊函数来定义对象和它们的特征。

#### 2. 构造函数

**构造函数**是一种特殊的函数，主要用来初始化对象，即为对象成员变量赋初始值，它总与 `new` 一起使用。我 们可以把对象中一些公共的属性和方法抽取出来，然后封装到这个函数里面。

`new` 在执行时会做四件事情：

① 在内存中创建一个新的空对象。

② 让 `this` 指向这个新的对象。

③ 执行构造函数里面的代码，给这个新对象添加属性和方法。

④ 返回这个新对象（所以构造函数里面不需要 `return` ）。

`JavaScript` 的构造函数中可以添加一些成员，可以在构造函数本身上添加，也可以在构造函数内部的 `this` 上添加。通过这两种方式添加的成员，就分别称为**静态成员**和**实例成员**。

**静态成员**：在构造函数本上添加的成员称为静态成员，<u>只能由构造函数本身来访问</u>

**实例成员**：在构造函数内部创建的对象成员称为实例成员，<u>只能由实例化的对象来访问</u>

```js
function Star(uname, age) {
    this.uname = uname;
    this.age = age; // 实例成员
}

Star.sex = '男'; // 静态成员
```

#### 3. 构造函数的问题

> 构造函数方法很好用，但是存在浪费内存的问题。

我们希望所有的对象使用同一个函数，这样就比较节省内存，那么我们要怎样做呢？

#### 4. 构造函数原型 prototype

构造函数通过原型分配的函数是所有对象所共享的。

JavaScript 规定，每一个构造函数都有一个 `prototype` 属性，指向另一个对象。注意这个 `prototype` 就是一 个对象，这个对象的所有属性和方法，都会被构造函数所拥有。

> 我们可以把那些不变的方法，直接定义在 `prototype` 对象上，这样所有对象的实例就可以共享这些方法。

```js
function Star(uname, age) {
    this.uname = uname;
    this.age = age;
}
Star.prototype.sing = function() { // 原型对象
    console.log('我会唱歌');
}
var ldh = new Star('刘德华', 18);
var zxy = new Star('张学友', 19);
console.log(ldh.sing === zxy.sing); // true
```

#### 5. 对象原型 proto

对象都会有一个属性 __proto__ 指向构造函数的 `prototype` 原型对象，之所以我们对象可以使用构造函数 `prototype` 原型对象的属性和方法，就是因为对象有 __proto__ 原型的存在。

```js
console.log(ldh.__proto__ === Star.prototype); // true
```

> 说明__proto__对象原型和原型对象 `prototype` 是等价的

__proto__对象原型的意义就在于为对象的查找机制提供一个方向，但是不可以使用这个属性。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/25/a8f5aa376d6aacacef54b6b59a88a87e.jpg" alt="a8f5aa376d6aacacef54b6b59a88a87e.jpg" border="0" />

**方法的查找规则**: 首先先看对象身上是否有对应方法,如果有就执行这个对象上的方法；如果没有这个方法,因为有__proto__ 的存在,就去构造函数原型对象`prototype`身上去查找这个方法。

#### 6. constructor 构造函数

对象原型（ `proto`）和构造函数（`prototype`）原型对象里面都有一个属性 `constructor` 属性 ，`constructor` 我们称为构造函数，因为它指回构造函数本身。

> `constructor` 主要用于<u>记录该对象引用于哪个构造函数</u>，它可以让原型对象重新指向原来的构造函数。

```js
Star.prototype = {
    // 如果我们修改了原来的原型对象,给原型对象赋值的是一个对象,则必须手动的利用constructor指回原来的构造函数
    constructor: Star,
    sing: function() {
        console.log('我会唱歌');
    },
    movie: function() {
        console.log('我会演电影');
    }
}
```

一般情况下，对象的方法都在构造函数的原型对象中设置。如果有多个对象的方法，我们可以给原型对象采取**对象形式**赋值，但是这样就会**覆盖**构造函数原型对象原来的内容，这样修改后的原型对象 `constructor` 就不再指向当前构造函数了。 此时，我们可以在修改后的原型对象中，<u>添加一个 `constructor`</u> 指向原来的构造函数。

#### 7. 构造函数、实例、原型对象三者之间的关系

<img src="https://img.zjgsuzjx.top/img/images/2021/06/26/db3bf680f56557821b7b6b9b988a1d7c.jpg" alt="db3bf680f56557821b7b6b9b988a1d7c.jpg" border="0" />

#### 8. 原型链

<img src="https://img.zjgsuzjx.top/img/images/2021/06/26/19d17e22623c55833320954416543a14.jpg" alt="19d17e22623c55833320954416543a14.jpg" border="0" />

#### 9. JavaScript 的成员查找机制(规则)

① 当访问一个对象的属性（包括方法）时，首先查找这个对象自身有没有该属性。

② 如果没有就查找它的原型（也就是 __proto__指向的 `prototype` 原型对象）。

③ 如果还没有就查找原型对象的原型（`Object`的原型对象）。

④ 依此类推一直找到 `Object` 为止（`null`）。

⑤ __proto__对象原型的意义就在于为对象成员查找机制提供一个方向，或者说一条路线。

```js
console.log(ldh.toString()); // 不报错
```

#### 10. 原型对象this指向

原型对象里面放的是方法, 这个方法里面的`this` 指向的是 这个<u>方法的调用者</u>, 也就是这个实例对象.

```js
function Star(uname, age) {
    this.uname = uname;
    this.age = age;
}
var that;
Star.prototype.sing = function() {
    console.log('我会唱歌');
    that = this;
}
var ldh = new Star('刘德华', 18);
ldh.sing();
console.log(that === ldh);
```

#### 11. 扩展内置对象

可以通过原型对象，对原来的内置对象进行扩展自定义的方法。比如给数组增加自定义求偶数和的功能。

```js
// 原型对象的应用 扩展内置对象方法
Array.prototype.sum = function() {
    var sum = 0;
    for (var i = 0; i < this.length; i++) {
        sum += this[i];
    }
    return sum;
};
var arr = [1, 2, 3];
console.log(arr.sum());
```

> 注意：数组和字符串内置对象不能给原型对象**覆盖**操作 `Array.prototype` = {} ，只能是 `Array.prototype.xxx` = `function`(){} 的方式。

### 二、ES5继承原理

ES6之前并没有给我们提供 `extends` 继承。我们可以通过构造函数+原型对象模拟实现继承，被称为组合继承。

#### 1. call()

调用这个函数, 并且修改函数运行时的 this 指向。

```js
// call 方法
function fn(x, y) {
    console.log(this);
    console.log(x + y);
}
var o = {
    name: 'andy'
};
// call() 可以改变这个函数的this指向 此时这个函数的this 就指向了o这个对象
fn.call(o, 1, 2); // 后面参数参与传递
```

#### 2. 借用构造函数继承父类型属性

**核心原理**： 通过 `call`() 把父类型的 `this` 指向子类型的 `this` ，这样就可以实现子类型<u>继承父类型的属性</u>。

```js
// 借用父构造函数继承属性
// 1. 父构造函数
function Father(uname, age) {
    // this 指向父构造函数的对象实例
    this.uname = uname;
    this.age = age;
}
// 2 .子构造函数 
function Son(uname, age, score) {
    // this 指向子构造函数的对象实例
    Father.call(this, uname, age);
    this.score = score;
}
var son = new Son('刘德华', 18, 100);
console.log(son);
```

#### 3. 借用原型对象继承父类型方法

一般情况下，对象的方法都在构造函数的原型对象中设置，通过构造函数无法继承父类方法。

**核心原理**：

① 将子类所共享的方法提取出来，让子类的 prototype 原型对象 = new 父类() 

② 本质：子类原型对象等于是实例化父类，因为父类实例化之后另外开辟空间，就不会影响原来父类原型对象

③ 将子类的 constructor 从新指向子类的构造函数

```js
// 借用父构造函数继承属性
// 1. 父构造函数
function Father(uname, age) {
    // this 指向父构造函数的对象实例
    this.uname = uname;
    this.age = age;
}
Father.prototype.money = function() {
    console.log(100000);
};
// 2 .子构造函数
function Son(uname, age, score) {
    // this 指向子构造函数的对象实例
    Father.call(this, uname, age);
    this.score = score;
}
// Son.prototype = Father.prototype;  这样直接赋值会有问题,如果修改了子原型对象,父原型对象也会跟着一起变化
Son.prototype = new Father();
// 如果利用对象的形式修改了原型对象,别忘了利用constructor 指回原来的构造函数
Son.prototype.constructor = Son;
// 这个是子构造函数专门的方法
Son.prototype.exam = function() {
    console.log('孩子要考试');
}
var son = new Son('刘德华', 18, 100);
```

<img src="https://img.zjgsuzjx.top/img/images/2021/06/26/7a81effba20e2d2fd0873b54f9abb335.jpg" alt="7a81effba20e2d2fd0873b54f9abb335.jpg" border="0" />

#### 4. ES6类的本质

- `class`本质还是`function`
- 类的所有方法都定义在类的`prototype`属性上
- 类创建的实例，里面也有`proto` 指向类的`prototype`原型对象
- 所以`ES6`的类它的绝大部分功能，`ES5`都可以做到，新的`class`写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已
- 所以`ES6`的类其实就是**语法糖.**
- **语法糖**：语法糖就是一种**便捷写法**。 简单理解, 有两种方法可以实现同样的功能，但是一种写法更加清晰、方便，那么这个方法就是语法糖

### 三、ES5 中的新增方法

#### 1. 数组方法

迭代(遍历)方法：`forEach`()、`map`()、`filter`()、`some`()、`every`()；

**forEach**：

`array.forEach(function(currentValue, index, arr))`

- `currentValue`：数组当前项的值
- `index`：数组当前项的索引
- `arr`：数组对象本身

```js
// forEach 迭代(遍历) 数组
var arr = [1, 2, 3];
var sum = 0;
arr.forEach(function(value, index, array) {
    console.log('每个数组元素' + value);
    console.log('每个数组元素的索引号' + index);
    console.log('数组本身' + array);
    sum += value;
})
console.log(sum);
```

**filter**：

`array.filter(function(currentValue, index, arr))`

- filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素，主要用于筛选数组
- 注意它直接返回一个**新数组**
- `currentValue`: 数组当前项的值
- `index`：数组当前项的索引
- `arr`：数组对象本身

```js
// filter 筛选数组
var arr = [12, 66, 4, 88, 3, 7];
var newArr = arr.filter(function(value, index) {
    // return value >= 20;
    return value % 2 === 0;
});
console.log(newArr);
```

**some**：

`array.some(function(currentValue, index, arr))`

- some() 方法用于检测数组中的元素<u>是否满足指定条件</u>。通俗点就是查找数组中是否有满足条件的元素
- 注意它返回值是布尔值, 如果查找到这个元素, 就返回true , 如果查找不到就返回false
- 如果<u>找到第一个满足条件的元素</u>，则终止循环，不再继续查找
- `currentValue`: 数组当前项的值
- `index`：数组当前项的索引
- `arr`：数组对象本身

```js
var arr1 = ['red', 'pink', 'blue'];
var flag1 = arr1.some(function(value) {
    return value == 'pink';
});
console.log(flag1);
```

**查询商品案例**：

- 把数据渲染到页面中 (forEach)
- 根据价格显示数据(filter)
- 根据商品名称显示数据

`forEach`和`some`的区别：

> 在`forEach`里面`return`不会终止迭代；在`some` 里面遇到`return` `true`就是终止遍历，迭代效率更高；`filter`里面`return`不会终止迭代

#### 2. 字符串方法

trim() 方法会从一个字符串的两端删除空白字符。

```js
// trim 方法去除字符串两侧空格
var str = '   an  dy   ';
console.log(str);
var str1 = str.trim();
console.log(str1); // 去除了空格
// 应用
var input = document.querySelector('input');
var btn = document.querySelector('button');
var div = document.querySelector('div');
btn.onclick = function() {
    var str = input.value.trim();
    if (str === '') {
        alert('请输入内容');
    } else {
        console.log(str);
        console.log(str.length);
        div.innerHTML = str;
    }
}
```

#### 3. 对象方法

1.`Object.keys()` 用于获取对象自身所有的属性

`Object.keys(obj)`

- 效果类似 for…in
- 返回一个由属性名组成的数组

```js
// 用于获取对象自身所有的属性
var obj = {
    id: 1,
    pname: '小米',
    price: 1999,
    num: 2000
};
var arr = Object.keys(obj);
console.log(arr);
```

> 相当于拷贝对象

2.`Object.defineProperty()` 定义新属性或修改原有的属性。

`Object.defineProperty(obj, prop, descriptor)`

- `obj`：必需。目标对象
- `prop`：必需。需定义或修改的属性的名字
- `descriptor`：必需。目标属性所拥有的特性

第三个参数 `descriptor` 说明： 以对象形式 `{ }` 书写

- `value`: 设置属性的值，默认为`undefined`
- `writable`: 值是否可以重写。`true` | `false` **默认**为`false` 
- `enumerable`: 目标属性是否可以被枚举。`true` | `false` 默认为 `false`
- `configurable`: 目标属性是否可以被删除或是否可以再次修改特性 `true` | `false` 默认为`false`

```js
// Object.defineProperty() 定义新属性或修改原有的属性
var obj = {
    id: 1,
    pname: '小米',
    price: 1999
};
Object.defineProperty(obj, 'address', {
    value: '中国山东蓝翔技校xx单元',
    // 如果只为false 不允许修改这个属性值 默认值也是false
    writable: false,
    // enumerable 如果值为false 则不允许遍历, 默认的值是 false
    enumerable: false,
    // configurable 如果为false 则不允许删除这个属性 不允许在修改第三个参数里面的特性 默认为false
    configurable: false
});
console.log(Object.keys(obj)); // 不能得到 address
delete obj.address; // 不能删除
obj.address = 2; // 不能修改
Object.defineProperty(obj, 'address', {
    configurable: true
});
console.log(obj.address); // 不能重新修改特性
```

## 三、函数进阶

### 一、函数的定义和调用

#### 1. 函数的定义方式补充

`var fn = new Function('参数1','参数2'..., '函数体')`

- `Function` 里面参数都必须是字符串格式
- 第三种方式执行效率低，也不方便书写，因此<u>较少使用</u> 
- 所有函数都是 `Function` 的实例(对象)
- 函数也属于对象

<img src="https://img.zjgsuzjx.top/img/images/2021/06/26/2dc1b6b23a45b6d4e639daf9072990d1.jpg" alt="2dc1b6b23a45b6d4e639daf9072990d1.jpg" border="0" />

```js
var f = new Function('a', 'b', 'console.log(a + b)');
f(1, 2);
// 4. 所有函数都是 Function 的实例(对象)
console.dir(f);
// 5. 函数也属于对象
console.log(f instanceof Object); // true
```

#### 2. 函数的调用方式总结

```js
// 1. 普通函数
function fn() {
    console.log('人生的巅峰');

}
fn();   // fn.call()
// 2. 对象的方法
var o = {
    sayHi: function() {
       //
    }
}
o.sayHi();
// 3. 构造函数
function Star() {};
new Star();
// 4. 绑定事件函数
 btn.onclick = function() {};   // 点击了按钮就可以调用这个函数
// 5. 定时器函数
setInterval(function() {}, 1000);  这个函数是定时器自动1秒钟调用一次
// 6. 立即执行函数
(function() {
    console.log('人生的巅峰');
})();
// 立即执行函数是自动调用
```

### 二、this

#### 1. 函数内 this 的指向

<img src="https://img.zjgsuzjx.top/img/images/2021/06/26/1adc5b854e4e87b8ab17f7e46d655f13.jpg" alt="1adc5b854e4e87b8ab17f7e46d655f13.jpg" border="0" />

#### 2. 改变函数内部 this 指向

JavaScript 为我们专门提供了一些函数方法来帮我们更优雅的处理函数内部 `this` 的指向问题，常用的有 `bind`()、 `call`()、`apply`() 三种方法。

**`call` 方法**：

`fun.call(thisArg, arg1, arg2, ...)` 

```js
function Father(uname, age, sex) {
    this.uname = uname;
    this.age = age;
    this.sex = sex;
}
function Son(uname, age, sex) {
    Father.call(this, uname, age, sex);
}
var son = new Son('刘德华', 18, '男');
```

> 因此当我们想改变 `this` 指向，同时想调用这个函数的时候，可以使用 `call`，比如继承

**`apply` 方法**：

`fun.apply(thisArg, [argsArray])`

`argsArray`：传递的值，必须包含在**数组**里面

```js
var arr = [1, 66, 3, 99, 4];
var max = Math.max.apply(Math, arr);
```

> `apply` 主要跟数组有关系，比如使用 `Math.max()` 求数组的最大值

**`bind` 方法**：

`bind()` 方法**不会调用函数**。但是能改变函数内部this 指向

`fun.bind(thisArg, arg1, arg2, ...)`

```js
var o = {
    name: 'andy'
};
function fn(a, b) {
    console.log(this);
    console.log(a + b);
};
var f = fn.bind(o, 1, 2);
f();
```

> 返回由指定的 `this` 值和初始化参数改造的原函数拷贝；因此当我们只是想改变 `this` 指向，并且不想调用这个函数的时候，可以使用 `bind`

```js
var btns = document.querySelectorAll('button');
let m;
for (var i = 0; i < btns.length; i++) {
    btns[i].onclick = function() {
        this.disabled = true;
        setTimeout(function() {
            this.disabled = false; // 这个this指向了btn[i]
        }.bind(this), 2000); // 用bind最合适
    }
}
```

> bind应用非常广泛，见[案例](https://www.bilibili.com/video/BV1Kt411w7MP?p=58)，定时器

#### 3. call apply bind 总结

**区别点**: 

1. `call` 和 `apply` 会调用函数, 并且改变函数内部`this`指向. 
2. `call` 和 `apply` 传递的参数不一样, `call` 传递参数 `aru1, aru2..`形式 `apply` 必须数组形式`[arg]`
3. `bind` 不会调用函数, 可以改变函数内部`this`指向.

**主要应用场景**: 

1. `call` 经常做<u>继承</u>
2. `apply` 经常跟数组有关系. 比如借助于数学对象实现数组<u>最大值最小值</u>
3. `bind` 不调用函数,但是还想改变this指向. 比如改变<u>定时器内部的this指向</u>

### 三、严格模式

#### 1. 什么是严格模式

`JavaScript` 除了提供正常模式外，还提供了严格模式（`strict mode`）。ES5 的严格模式是采用具有限制性 `JavaScript` 变体的一种方式，即在严格的条件下运行 JS 代码。

严格模式对正常的 `JavaScript` 语义做了一些更改： 

1. 消除了 `Javascript` 语法的一些不合理、不严谨之处，减少了一些怪异行为。
2. 消除代码运行的一些不安全之处，保证代码运行的安全。
3. 提高编译器效率，增加运行速度。
4. 禁用了在 `ECMAScript` 的未来版本中可能会定义的一些语法，为未来新版本的 Javascript 做好铺垫。比 如一些保留字如：`class`, `enum`, `export`, `extends`, `import`, `super` 不能做变量名

#### 2. 开启严格模式

严格模式可以应用到整个脚本或个别函数中。因此在使用时，我们可以将严格模式分为为**脚本**开启严格模式和为**函数**开启严格模式两种情况。

**为脚本开启严格模式**：

为整个脚本文件开启严格模式，需要在所有语句之前放一个特定语句`“use strict”;（或‘use strict’;）`。

```js
<script>
    'use strict';
    //
</script>
```

<u>有的 `script` 基本是严格模式，有的 `script` 脚本是正常模式</u>，这样不利于文件合并，所以可以将整个脚本文件 放在一个<u>立即执行的匿名函数</u>之中。这样独立创建一个作用域而不影响其他 `script` 脚本文件。

```js
<script>
    (function (){
        "use strict";
        var num = 10;
        function fn() {}
    })();
</script>
```

**为函数开启严格模式**：

要给某个函数开启严格模式，需要把`“use strict”; (或 'use strict'; )` 声明放在函数体所有语句之前。

```js
function fn(){
    "use strict";
    return "这是严格模式。";
}
```

> 将 `"use strict"` 放在函数体的第一行，则整个函数以 "严格模式" 运行

#### 3. 严格模式中的变化

**变量规定**：

① 在正常模式中，如果一个变量没有声明就赋值，默认是全局变量。严格模式禁止这种用法，<u>变量都必须先用 `var` 命令声明</u>，然后再使用。

② <u>严禁删除已经声明变量</u>。例如，`delete x;` 语法是错误的。

**this 指向问题**：

① 以前在全局作用域函数中的 `this` 指向 `window` 对象。

② 严格模式下全局作用域中函数中的 `this`是 `undefined`。

③ 以前构造函数时不加`new`也可以调用,当普通函数，`this` 指向全局对象

④ 严格模式下,如果构造函数不加`new`调用, `this` 指向的是`undefined` 如果给他赋值则会报错

⑤ `new` 实例化的构造函数指向创建的对象实例。

⑥ 定时器 `this` 还是指向 `window` 。

⑦ 事件、对象还是指向调用者。

**函数变化**：

① 函数<u>不能有重名</u>的参数。

② 函数必须声明在顶层。为了与新版本接轨，<u>不允许在非函数的代码块内声明函数</u>。

更多严格模式要求参考：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode

### 四、高阶函数

高阶函数是对其他函数进行操作的函数，它接收<u>函数作为参数</u>或<u>将函数作为返回值</u>输出。

```js
function fn(callback){
    callback&&callback();
}
fn(function(){alert('hi')}) // 函数作为参数
```

```js
function fn(){
    return function() {} // 返回一个函数
}
fn();
```

> 最典型的就是作为回调函数。

### 五、闭包

#### 1. 什么是闭包

闭包（`closure`）指有权访问另一个函数作用域中变量的**函数**。 ----- `JavaScript` 高级程序设计

> 简单理解就是 ，一个作用域可以访问另外一个函数内部的局部变量。

```js
function fn1(){ // fn1 就是闭包函数
    var num = 10;
    function fn2(){
        console.log(num); // 10
    }
    fn2()
}
fn1();
```

#### 2. 在 chrome 中调试闭包

1. 打开浏览器，按 F12 键启动 chrome 调试工具。 
2. 设置断点。
3. 找到 Scope 选项（Scope 作用域的意思）。
4. 当我们重新刷新页面，会进入断点调试，Scope 里面会有两个参数（global 全局作用域、local 局部作用域）。
5. 当执行到 fn2() 时，Scope 里面会多一个 Closure 参数 ，这就表明产生了闭包。

#### 3. 闭包的作用

> 延伸变量的作用范围。

```js
function fn() {
    var num = 10;
    return function {
        console.log(num); // 10 
    }
}
var f = fn();
f()
```

#### 4. 闭包案例

**循环注册点击事件**：

```js
// 利用闭包的方式得到当前小li 的索引号
for (var i = 0; i < lis.length; i++) {
    // 利用for循环创建了4个立即执行函数
    // 立即执行函数也成为小闭包因为立即执行函数里面的任何一个函数都可以使用它的i这变量
    (function(i) {
        // console.log(i);
        lis[i].onclick = function() {
            console.log(i);
        }
    })(i);
}
```

**循环中的 setTimeout()**：

```js
// 闭包应用-3秒钟之后,打印所有li元素的内容
var lis = document.querySelector('.nav').querySelectorAll('li');
for (var i = 0; i < lis.length; i++) {
    (function(i) {
        setTimeout(function() {
            console.log(lis[i].innerHTML);
        }, 3000)
    })(i);
}
```

**计算打车价格**：

```js
// 打车起步价13(3公里内),  之后每多一公里增加 5块钱.  用户输入公里数就可以计算打车价格
// 如果有拥堵情况,总价格多收取10块钱拥堵费
```

```js
// 闭包应用-计算打车价格
var car = (function() {
    var start = 13; // 起步价  局部变量
    var total = 0; // 总价  局部变量
    return {
        // 正常的总价
        price: function(n) {
            if (n <= 3) {
                total = start;
            } else {
                total = start + (n - 3) * 5;
            }
            return total;
        },
        // 拥堵之后的费用
        yd: function(flag) {
            return flag ? total + 10 : total;
        }
    }
})();
console.log(car.price(5)); // 23
console.log(car.yd(true)); // 33

console.log(car.price(1)); // 13
console.log(car.yd(false)); // 13
```

**思考题**：

```js
// 思考题 1：
var name = "The Window";
var object = {
    name: "My Object",
    getNameFunc: function() {
        return function() {
            return this.name;
        };
    }
};

console.log(object.getNameFunc()()) // The Window
```

```js
// 思考题 2：
var name = "The Window";　　
var object = {　　　　
    name: "My Object",
    getNameFunc: function() {
        var that = this;
        return function() {
            return that.name;
        };
    }
};

console.log(object.getNameFunc()()) // My Object
```

### 六、递归

#### 1. 什么是递归

如果一个函数在内部可以调用其本身，那么这个函数就是**递归函数**。

> **简单理解**:函数内部自己调用自己, 这个函数就是递归函数

由于递归很容易发生“**栈溢出**”错误（`stack overflow`），所以必须要加退出条件 `return`。

#### 2. 递归求数学题

**求阶乘**：

```js
function fn(num) {
    if(num===1) return 1;
    return num*fn(num-1);
}
```

**求斐波那契数列**：

```js
function fn(num) {
    if(num===1||num===2){
        return 1;
    }
    return fn(num-1)+fn(num-2);
}
```

**根据id返回对应的数据对象**：

```js
var data = [{
    id: 1,
    name: '家电',
    goods: [{
        id: 11,
        gname: '冰箱'
    }]
}, {
    id: 2,
    name: '服饰'
}];
function getID(json, id) {
    var o = {};
    json.forEach(function(item) {
        if (item.id == id) {
            o = item;
            // 我们想要得里层的数据 11 12 可以利用递归函数
            // 里面应该有goods这个数组并且数组的长度不为 0 
        } else if (item.goods && item.goods.length > 0) {
            o = getID(item.goods, id); // 接受retrun的值
        }
    });
    return o;
}
```

#### 3. 浅拷贝和深拷贝

1. 浅拷贝只是拷贝一层，更深层次对象级别的只拷贝**引用**
2. 深拷贝拷贝多层，每一级别的数据都会拷贝

> es6新增方法可以**浅拷贝**：`Object.assign(target, ...sources)`

```js
Object.assign(o, obj); // obj浅拷贝给o
```

**利用原生JS实现深拷贝**：

```js
// 深拷贝拷贝多层, 每一级别的数据都会拷贝.
var obj = {
    id: 1,
    name: 'andy',
    msg: {
        age: 18
    },
    color: ['pink', 'red']
};
var o = {};
// 封装函数
function deepCopy(newobj, oldobj) {
    for (var k in oldobj) {
        // 判断我们的属性值属于那种数据类型
        // 1. 获取属性值  oldobj[k]
        var item = oldobj[k];
        // 2. 判断这个值是否是数组
        if (item instanceof Array) {
            newobj[k] = [];
            deepCopy(newobj[k], item)
        } else if (item instanceof Object) {
            // 3. 判断这个值是否是对象
            newobj[k] = {};
            deepCopy(newobj[k], item)
        } else {
            // 4. 属于简单数据类型
            newobj[k] = item;
        }

    }
}
deepCopy(o, obj);
console.log(o);
```

## 四、正则表达式

### 一、概述

#### 1. 含义及用途

正则表达式（ `Regular Expression` ）是用于匹配字符串中字符组合的模式。在 JavaScript中，正则表达式也 是对象。

例如**验证表单**：用户名表单只能输入英文字母、数字或者下划线， 昵称输入框中可以输入中文(匹配)。此外，正则表达式还常用于过**滤掉**页面内容中的一些敏感词(替换)，或从字符串中获取我们想要的特定部分(**提取**)等 。

#### 2. 特点

1. 灵活性、逻辑性和功能性非常的强。
2. 可以迅速地用极简单的方式达到字符串的复杂控制。
3. 实际开发,一般都是直接复制写好的正则表达式.

### 二、正则表达式在 JavaScript 中的使用

#### 1. 创建正则表达式

在 JavaScript 中，可以通过两种方式创建一个正则表达式。

- 通过调用 RegExp 对象的构造函数创建

```js
var 变量名 = new RegExp(/表达式/);
```

-  通过字面量创建


```js
var 变量名 = /表达式/;
```

#### 2. 测试正则表达式 test

`test`() 正则对象方法，用于检测字符串是否符合该规则，该对象会返回 `true` 或 `false`，其参数是测试字符串。

`regexObj.test(str)`

`regexObj`：是写的正则表达式

`str`：我们要测试的文本

```js
var rg = /123/;
console.log(rg.test(123)); // true
console.log(rg.test('abc')); // false
```

### 三、正则表达式中的特殊字符

#### 1. 正则表达式的组成

一个正则表达式可以由简单的字符构成，比如 `/abc/`，也可以是简单和特殊字符的组合，比如 `/ab*c/` 。其中 特殊字符也被称为元字符，在正则表达式中是具有特殊意义的专用符号，如 `^ 、$ 、+` 等。

MDN：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions

正则测试工具: http://tool.oschina.net/regex

#### 2. 边界符

正则表达式中的边界符（位置符）用来提示字符所处的位置，主要有两个字符。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/27/391463851b7b0db748f558f90495f65d.jpg" alt="391463851b7b0db748f558f90495f65d.jpg" border="0" />

> 如果 `^` 和 `$` 在一起，表示必须是精确匹配。

```js
var rg = /abc/; 
console.log(rg.test('abc'));
console.log(rg.test('abcd'));
console.log(rg.test('aabcd'));

var reg = /^abc/;
console.log(reg.test('abc')); // true
console.log(reg.test('abcd')); // true
console.log(reg.test('aabcd')); // false

var reg1 = /^abc$/; 
console.log(reg1.test('abc')); // true
console.log(reg1.test('abcd')); // false
console.log(reg1.test('aabcd')); // false
console.log(reg1.test('abcabc')); // false
```

#### 3. 字符类

字符类表示有一系列字符可供选择，只要匹配其中一个就可以了。<u>所有可供选择的字符都放在方括号内</u>。

 **[] 方括号**：

`/[abc]/.test('andy') // true`

> 后面的字符串只要包含 abc 中任意一个字符，都返回 true 。

```js
var rg = /[abc]/; // 只要包含有a 或者 包含有b 或者包含有c 都返回为true
console.log(rg.test('andy')); // true
console.log(rg.test('red')); // false

var rg1 = /^[abc]$/; // 三选一 只有是a 或者是 b  或者是c 这三个字母才返回 true
console.log(rg1.test('aa')); // false
console.log(rg1.test('a')); // true
console.log(rg1.test('b'));// true
console.log(rg1.test('c'));// true
console.log(rg1.test('abc'));// false
```

**[-] 方括号内部 范围符-**：

`/^[a-z]$/.test(c') // true`

> 方括号内部加上 `-` 表示范围，这里表示 a 到 z 26个英文字母都可以。

```js
// 26个英文字母任何一个字母返回 true  - 表示的是a 到z 的范围
var reg = /^[a-z]$/;   
console.log(reg.test('a')); // true
console.log(reg.test('z')); // true
console.log(reg.test(1)); // false
console.log(reg.test('A')); // false
```

**[^] 方括号内部 取反符^**：

```js
// 如果中括号里面有^ 表示取反的意思 千万和 我们边界符 ^ 别混淆
var reg2 = /^[^a-zA-Z0-9_-]$/;
console.log(reg2.test('a')); // false
console.log(reg2.test('B')); // false
console.log(reg2.test(8)); // false
console.log(reg2.test('-')); // false
console.log(reg2.test('_')); // false
console.log(reg2.test('!')); // true
```

> 注意和边界符 `^` 区别，边界符写到方括号外面。

**字符组合**：

```js
// 字符组合
var reg1 = /^[a-zA-Z0-9_-]$/; // 26个英文字母(大写和小写都可以)任何一个字母返回 true  
console.log(reg1.test('a')); // true
console.log(reg1.test('B')); // true
console.log(reg1.test(8)); // true
console.log(reg1.test('-')); // true
console.log(reg1.test('_')); // true
console.log(reg1.test('!')); // false
```

> 方括号内部可以使用字符组合，这里表示包含 a 到 z 的26个英文字母和 1 到 9 的数字都可以。

#### 4. 量词符

量词符用来设定某个模式出现的**次数**。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/27/39ce782dfb0930e7798720b7452067a1.jpg" alt="39ce782dfb0930e7798720b7452067a1.jpg" border="0" />

```js
// * 相当于 >= 0 可以出现0次或者很多次
var reg = /^a*$/;
console.log(reg.test('')); // true
console.log(reg.test('aaaa')); // true

//  + 相当于 >= 1 可以出现1次或者很多次
var reg = /^a+$/;
console.log(reg.test('')); // false
console.log(reg.test('a')); // true
console.log(reg.test('aaaa')); // true

//  ?  相当于 1 || 0
var reg = /^a?$/;
console.log(reg.test('')); // true
console.log(reg.test('a')); // true
console.log(reg.test('aaaa')); // false

//  {3 } 就是重复3次
var reg = /^a{3}$/;
console.log(reg.test('')); // false
console.log(reg.test('aaaa')); // false
console.log(reg.test('aaa')); // true

//  {3, }  大于等于3
var reg = /^a{3,}$/;
console.log(reg.test('')); // false
console.log(reg.test('aaaa')); // true
console.log(reg.test('aaa')); // true

//  {3,16}  大于等于3 并且 小于等于16
var reg = /^a{3,6}$/;
console.log(reg.test('')); // false
console.log(reg.test('aaaa')); // true
console.log(reg.test('aaa')); // true
console.log(reg.test('aaaaaaa')); // false
```

**用户名验证**：

**要求**：用户名只能为英文字母,数字,下划线或者短横线组成, 并且用户名长度为 6~16位

```js
var reg = /^[a-zA-Z0-9_-]{6,16}$/;
var uname = document.querySelector('.uname');
var span = document.querySelector('span');
uname.onblur = function() { // 失去焦点
    if (reg.test(this.value)) {
        console.log('正确的');
        span.className = 'right';
        span.innerHTML = '用户名格式输入正确';
    } else {
        console.log('错误的');
        span.className = 'wrong';
        span.innerHTML = '用户名格式输入不正确';
    }
}
```

#### 5. 括号总结

**大括号**：量词符 里面表示重复次数

**中括号**：字符集合。匹配方括号中的任意字符

**小括号**：表示优先级

> 可以在线测试: https://c.runoob.com/

```js
// 小括号 表示优先级
var reg = /^(abc){3}$/; // 它是让abcc重复三次
console.log(reg.test('abc'));
console.log(reg.test('abcabcabc'));
console.log(reg.test('abccc'));
```

#### 6. 预定义类

预定义类指的是某些常见模式的简写方式。

<img src="https://img.zjgsuzjx.top/img/images/2021/06/28/8cb40e834d20d11bff5fe7475e09d2ca.jpg" alt="8cb40e834d20d11bff5fe7475e09d2ca.jpg" border="0" />

**座机号码验证**：

```js
var reg = /^\d{3,4}-\d{7,8}$/;
```

**常用的表单验证正则表达式**：

```js
手机号码: /^1[3|4|5|7|8][0-9]{9}$/
QQ: [1-9][0-9]{4,} (腾讯QQ号从10000开始)
昵称是中文: ^[\u4e00-\u9fa5]{2,8}$
```

### 四、正则表达式中的替换

#### 1. replace 替换

replace() 方法可以实现替换字符串操作，用来替换的参数可以是一个字符串或是一个正则表达式。

`stringObject.replace(regexp/substr,replacement)`

- 第一个参数: 被替换的<u>字符串</u> 或者 <u>正则表达式</u>
- 第二个参数: 替换为的字符串
- <u>返回值是一个替换完毕的新字符串</u>

#### 2. 正则表达式参数

`/表达式/[switch]`

switch(也称为修饰符) 按照什么样的模式来匹配. 有三种值：

- `g`：全局匹配
- `i`：忽略大小写
- `gi`：全局匹配 + 忽略大小写

**敏感词过滤案例**：

```js
var text = document.querySelector('textarea');
var btn = document.querySelector('button');
var div = document.querySelector('div');
btn.onclick = function() {
    div.innerHTML = text.value.replace(/激情|gay/g, '**');
}
```










