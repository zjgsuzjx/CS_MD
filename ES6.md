## let 和 const 命令

### let 命令

#### 基本用法

ES6 新增了`let`命令，用来**声明变量**。它的用法类似于`var`，但是所声明的变量，只在`let`命令所在的**代码块内**有效。

```javascript
{
  let a = 10;
  var b = 1;
}
a // ReferenceError: a is not defined.
b // 1
```

> `let`声明的变量只在它所在的代码块有效。

`for`循环的计数器，就很合适使用`let`命令。

```javascript
for (let i = 0; i < 10; i++) {
  	console.log("zjgsuzjx");
}
console.log(i);
// ReferenceError: i is not defined
```

另外，`for`循环还有一个特别之处，就是设置循环变量的那部分是一个**父作用域**，而循环体内部是一个单独的**子作用域**。

```javascript
for (let i = 0; i < 3; i++) {
  let i = 'abc';
  console.log(i);
}
// abc
// abc
// abc
```

> 上面代码正确运行，这表明函数内部的变量`i`与循环变量`i`不在同一个作用域，有各自**单独的作用域**。

#### 不存在变量提升

`var`命令会发生“**变量提升**”现象，即变量可以在声明之前使用，值为`undefined`。为了纠正这种现象，`let`命令改变了语法行为，它所声明的变量一定要在声明后使用，否则报错。

```javascript
// var 的情况
console.log(foo); // 输出undefined
var foo = 2;

// let 的情况
console.log(bar); // 报错ReferenceError
let bar = 2;
```

#### 暂时性死区

只要**块级作用域**内存在`let`命令，它所声明的变量就“绑定”（binding）这个区域，<u>不再受外部的影响</u>。

```js
var tmp = 123;

function fn() {
    tmp='123';	// ReferenceError
    console.log(tmp);
    let tmp;
}
fn();
```

上面代码中，存在全局变量`tmp`，但是块级作用域内`let`又声明了一个局部变量`tmp`，导致后者绑定这个块级作用域，所以在`let`声明变量前，对`tmp`赋值会报错。

> ES6 明确规定，如果区块中存在`let`和`const`命令，这个区块对这些命令声明的变量，从一开始就形成了**封闭作用域**。凡是在声明之前就使用这些变量，就会报错。

```js
if(true){
    console.log(typeof x); // 报错
    let x;
}

if(true){
     console.log(typeof x); // 输出undefined
}
```

另外，下面的代码也会报错，与`var`的行为不同。

```javascript
// 不报错
var x = x;

// 报错
let x = x;
// ReferenceError: x is not defined
```

> 上面代码报错，也是因为暂时性死区。使用`let`声明变量时，只要变量在还没有声明完成前使用，就会报错。

暂时性死区的**本质**就是，只要一进入**当前作用域**，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。

#### 不允许重复声明

`let`不允许在相同作用域内，重复声明同一个变量。

```javascript
// 报错
function func() {
  let a = 10;
  var a = 1;
}

// 报错
function func() {
  let a = 10;
  let a = 1;
}
```

### 块级作用域

#### 为什么需要块级作用域

ES5 只有全局作用域和函数作用域，没有块级作用域，这带来很多不合理的场景。

```javascript
var tmp = new Date();

function f() {
  console.log(tmp);
  if (false) {
    var tmp = 'hello world';
  }
}

f(); // undefined
```

上面代码的原意是，`if`代码块的外部使用外层的`tmp`变量，内部使用内层的`tmp`变量。但是，函数`f`执行后，输出结果为`undefined`，原因在于**变量提升**，导致内层的`tmp`变量覆盖了外层的`tmp`变量。

#### ES6 的块级作用域

`let`实际上为 JavaScript 新增了块级作用域。

```javascript
function f1() {
  let n = 5;
  if (true) {
    let n = 10;
  }
  console.log(n); // 5
}
```

以上代码表示外层代码块不受内层代码块的影响。如果两次都使用`var`定义变量`n`，最后输出的值才是 10。

`let`的块级作用域包括`if`、`while`、`for`等。

### const 命令

`const`声明一个只读的常量。一旦声明，常量的值就**不能改变**。

```javascript
const PI = 3.1415;
PI // 3.1415

PI = 3;
// TypeError: Assignment to constant variable.
```

`const`声明的变量不得改变值，这意味着，`const`一旦声明变量，就必须**立即初始化**，不能留到以后赋值。

```javascript
const foo;
// SyntaxError: Missing initializer in const declaration
```

`const`的作用域与`let`命令相同：只在声明所在的块级作用域内有效。

```javascript
if (true) {
  const MAX = 5;
}

MAX // Uncaught ReferenceError: MAX is not defined
```

> `const`命令声明的常量也是不提升，同样存在暂时性死区，只能在声明的位置后面使用。也与`let`一样不可重复声明。

#### const 的本质

`const`实际上保证的，并不是变量的值不得改动，而是变量指向的那个**内存地址**所保存的数据不得改动。

对于**简单类型**的数据（数值、字符串、布尔值），值就保存在变量指向的那个内存地址，因此等同于**常量**。

对于**复合类型**的数据（主要是<u>对象和数组</u>），变量指向的内存地址，保存的只是一个指向实际数据的指针，`const`只能保证这个指针是固定的（即总是指向另一个固定的地址）。

```javascript
const foo = {};

// 为 foo 添加一个属性，可以成功
foo.prop = 123;
foo.prop // 123

// 将 foo 指向另一个对象，就会报错
foo = {}; // TypeError: "foo" is read-only
```

> 以上代码说明，不可变的只是这个地址，即不能把`foo`指向另一个地址，但对象本身是可变的，所以依然可以为其添加新属性。

### 顶层对象的属性

顶层对象，在浏览器环境指的是`window`对象。ES5 之中，顶层对象的属性与全局变量是**等价**的。

```javascript
var a = 1;
window.a // 1
a = 2;
window.a // 2
```

这非常不利于模块化编程，ES6 为了改变这一点，`let`命令、`const`命令、`class`命令声明的全局变量，不属于顶层对象的属性。

```javascript
let b = 1;
window.b // undefined
```

> 也就是说，从 ES6 开始，全局变量将逐步与顶层对象的属性脱钩。

## 变量的解构赋值

### 数组的解构赋值

#### 基本用法

ES6 允许按照一定模式，从数组和对象中提取值，对**变量**进行赋值，这被称为**解构**（Destructuring）。

```javascript
let a = 1;
let b = 2;
let c = 3;
// ES6 允许写成下面这样
let [a, b, c] = [1, 2, 3];
```

> 上面代码表示，可以从数组中提取值，按照对应位置，对变量赋值。

本质上，这种写法属于“**模式匹配**”，只要等号两边的模式相同，左边的变量就会被赋予对应的值。下面是一些使用嵌套数组进行解构的例子。

```javascript
let [foo, [[bar], baz]] = [1, [[2], 3]];
foo // 1
bar // 2
baz // 3

let [ , , third] = ["foo", "bar", "baz"];
third // "baz"

let [x, y] = [1, 2, 3];
x // 1
y // 2

let [head, ...tail] = [1, 2, 3, 4];
head // 1
tail // [2, 3, 4]

let [x, y, ...z] = ['a'];
x // "a"
y // undefined
z // []

let [a, [b], d] = [1, [2, 3], 4];
a // 1
b // 2
d // 4
```

> 如果解构不成功，变量的值就等于`undefined`。

#### 默认值

解构赋值允许指定默认值。

```javascript
let [foo = true] = [];
foo // true

let [x, y = 'b'] = ['a']; // x='a', y='b'
let [x, y = 'b'] = ['a', undefined]; // x='a', y='b'
```

### 对象的解构赋值

#### 简介

解构不仅可以用于数组，还可以用于**对象**。

```javascript
let { foo, bar } = { foo: 'aaa', bar: 'bbb' };
foo // "aaa"
bar // "bbb"
```

对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由它的**位置**决定；而对象的属性**没有次序**，变量必须与属性同名，才能取到正确的值。

```javascript
let { bar, foo } = { foo: 'aaa', bar: 'bbb' };
foo // "aaa"
bar // "bbb"

let { baz } = { foo: 'aaa', bar: 'bbb' };
baz // undefined
```

> 对象的解构赋值的内部机制，是先找到同名属性，然后再赋给对应的变量。真正被赋值的是**后者**，而**不是前者**。

```javascript
let { foo: baz } = { foo: 'aaa', bar: 'bbb' };
baz // "aaa"
foo // error: foo is not defined
```

#### 默认值

对象的解构也可以指定默认值。

```javascript
var {x = 3} = {};
x // 3

var {x, y = 5} = {x: 1};
x // 1
y // 5

var {x: y = 3} = {};
y // 3

var {x: y = 3} = {x: 5};
y // 5

var { message: msg = 'Something went wrong' } = {};
msg // "Something went wrong"
```

### 字符串的解构赋值

字符串也可以解构赋值。这是因为此时，字符串被转换成了一个类似数组的对象。

```javascript
const [a, b, c, d, e] = 'hello';
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"
```

类似数组的对象都有一个`length`属性，因此还可以对这个属性解构赋值。

```javascript
let {length : len} = 'hello';
len // 5
```

### 函数参数的解构赋值

函数的参数也可以使用解构赋值。

```javascript
function add([x, y]){
  return x + y;
}

add([1, 2]); // 3
```

函数参数的解构也可以使用默认值。

```javascript
function move({x = 0, y = 0} = {}) {
  return [x, y];
}

move({x: 3, y: 8}); // [3, 8]
move({x: 3}); // [3, 0]
move({}); // [0, 0]
move(); // [0, 0]
```

### 解构赋值的用途

#### 交换变量的值

```javascript
let x = 1;
let y = 2;

[x, y] = [y, x];
```

> 上面代码交换变量`x`和`y`的值，这样的写法不仅简洁，而且易读，语义非常清晰。

#### 从函数返回多个值

函数只能返回一个值，如果要返回多个值，只能将它们放在**数组**或**对象**里返回。有了解构赋值，取出这些值就非常方便。

```javascript
// 返回一个数组

function example() {
  return [1, 2, 3];
}
let [a, b, c] = example();

// 返回一个对象

function example() {
  return {
    foo: 1,
    bar: 2
  };
}
let { foo, bar } = example();
```

#### 函数参数的定义

解构赋值可以方便地将一组参数与变量名对应起来。

```javascript
// 参数是一组有次序的值
function f([x, y, z]) { ... }
f([1, 2, 3]);

// 参数是一组无次序的值
function f({x, y, z}) { ... }
f({z: 3, y: 2, x: 1});
```

## 字符串的拓展

### 模板字符串

模板字符串（template string）是增强版的字符串，用反引号（`）标识。它可以当作普通字符串使用，也可以用来定义多行字符串，或者在字符串中嵌入变量。

```javascript
// 字符串中嵌入变量
let name = "Bob", time = "today";
`Hello ${name}, how are you ${time}?`
```

如果在模板字符串中需要使用反引号，则前面要用反斜杠转义。

```javascript
let greeting = `\`Yo\` World!`;
```

> 如果使用模板字符串表示多行字符串，所有的**空格**和**缩进**都会被保留在输出之中。

## 字符串的新增方法

### 索引方法

传统上，JavaScript 只有`indexOf`方法，可以用来确定一个字符串是否包含在另一个字符串中。ES6 又提供了三种新方法。

> 这三个方法都支持第二个参数，表示开始搜索的位置。

- **includes()**：返回布尔值，表示是否找到了参数字符串。

```javascript
let s = 'Hello world!';
s.includes('o') // true
s.includes('Hello', 6) // false
```

- **startsWith()**：返回布尔值，表示参数字符串是否在原字符串的头部。

```javascript
let s = 'Hello world!';
s.startsWith('Hello') // true
s.startsWith('world', 6) // true
```

- **endsWith()**：返回布尔值，表示参数字符串是否在原字符串的尾部。

```javascript
let s = 'Hello world!';
s.endsWith('!') // true
s.endsWith('Hello', 5) // true
```

使用第二个参数`n`时，`endsWith`的行为与其他两个方法有所不同。它针对前`n`个字符，而其他两个方法针对从第`n`个位置直到字符串结束。

### 重复字符串方法

`repeat`方法返回一个新字符串，表示将原字符串重复`n`次。

```javascript
'x'.repeat(3) // "xxx"
'hello'.repeat(2) // "hellohello"
'na'.repeat(0) // ""
```

> 参数如果是小数，会被取整。

```javascript
'na'.repeat(2.9) // "nana"
```

但是，如果参数是 0 到-1 之间的小数，则等同于 0，这是因为会先进行取整运算。0 到-1 之间的小数，取整以后等于`-0`，`repeat`视同为 0。

```javascript
'na'.repeat(-0.9) // ""
```

如果`repeat`的参数是负数或者`Infinity`，会报错。

```javascript
'na'.repeat(Infinity)
// RangeError
'na'.repeat(-1)
// RangeError
```

### 字符串补长方法

ES2017 引入了字符串补全长度的功能。如果某个字符串不够指定长度，会在头部或尾部补全。`padStart()`用于头部补全，`padEnd()`用于尾部补全。

```javascript
'x'.padStart(5, 'ab') // 'ababx'
'x'.padStart(4, 'ab') // 'abax'

'x'.padEnd(5, 'ab') // 'xabab'
'x'.padEnd(4, 'ab') // 'xaba'
```

上面代码中，`padStart()`和`padEnd()`一共接受两个参数，第一个参数是字符串补全生效的最大长度，第二个参数是用来补全的字符串。

> 如果原字符串的长度，等于或大于最大长度，则字符串补全不生效，返回原字符串。

```javascript
'xxx'.padStart(2, 'ab') // 'xxx'
'xxx'.padEnd(2, 'ab') // 'xxx'
```

> 如果用来补全的字符串与原字符串，两者的长度之和超过了最大长度，则会截去超出位数的补全字符串。

```javascript
'abc'.padStart(10, '0123456789')
// '0123456abc'
```

> 如果省略第二个参数，默认使用空格补全长度。

### 字符串替换方法

历史上，字符串的实例方法`replace()`只能替换第一个匹配。

```javascript
'aabbcc'.replace('b', '_')
// 'aa_bcc'
```

[ES2021](https://github.com/tc39/proposal-string-replaceall) 引入了`replaceAll()`方法，可以一次性替换所有匹配。

```javascript
'aabbcc'.replaceAll('b', '_')
// 'aa__cc'
```

`replaceAll()`的第二个参数`replacement`是一个字符串，表示替换的文本，其中可以使用一些特殊字符串。

- `$&`：匹配的子字符串。
- `$` `：匹配结果前面的文本。
- `$'`：匹配结果后面的文本。
- `$n`：匹配成功的第`n`组内容，`n`是从1开始的自然数。这个参数生效的前提是，第一个参数必须是正则表达式。
- `$$`：指代美元符号`$`。

```javascript
// $& 表示匹配的字符串，即`b`本身
// 所以返回结果与原字符串一致
'abbc'.replaceAll('b', '$&')
// 'abbc'

// $` 表示匹配结果之前的字符串
// 对于第一个`b`，$` 指代`a`
// 对于第二个`b`，$` 指代`ab`
'abbc'.replaceAll('b', '$`')
// 'aaabc'

// $' 表示匹配结果之后的字符串
// 对于第一个`b`，$' 指代`bc`
// 对于第二个`b`，$' 指代`c`
'abbc'.replaceAll('b', `$'`)
// 'abccc'

// $1 表示正则表达式的第一个组匹配，指代`ab`
// $2 表示正则表达式的第二个组匹配，指代`bc`
'abbc'.replaceAll(/(ab)(bc)/g, '$2$1')
// 'bcab'

// $$ 指代 $
'abc'.replaceAll('b', '$$')
// 'a$c'
```

## 函数的扩展

### 函数参数的默认值

#### 基本用法

ES6 之前，不能直接为函数的参数指定默认值，只能采用变通的方法。

```javascript
function log(x, y) {
  y = y || 'World';
  console.log(x, y);
}

log('Hello') // Hello World
log('Hello', 'China') // Hello China
log('Hello', '') // Hello World
```

上面代码检查函数`log`的参数`y`有没有赋值，如果没有，则指定默认值为`World`。这种写法的**缺点**在于，如果参数`y`赋值了，但是对应的布尔值为`false`，则该赋值不起作用。就像上面代码的最后一行，参数`y`等于<u>空字符</u>，结果<u>被改为默认值</u>。

ES6 允许为函数的参数设置**默认值**，即直接写在参数定义的后面。

```javascript
function log(x, y = 'World') {
  console.log(x, y);
}

log('Hello') // Hello World
log('Hello', 'China') // Hello China
log('Hello', '') // Hello
```

> 参数变量是默认声明的，所以不能用`let`或`const`再次声明。

```javascript
function foo(x = 5) {
  let x = 1; // error
  const x = 2; // error
}
```

### rest 参数

ES6 引入 rest 参数（形式为`...变量名`），用于获取函数的多余参数，这样就不需要使用`arguments`对象了。rest 参数搭配的变量是一个数组，该变量将多余的参数放入数组中。

```javascript
function add(...values) {
  let sum = 0;
  for (var val of values) {
    sum += val;
  }
  return sum;
}

add(2, 5, 3) // 10
```

上面代码的`add`函数是一个求和函数，利用 rest 参数，可以向该函数传入任意数目的参数。

> `for of` 遍历数组；`for in` 遍历对象
>
> **注意**：rest 参数之后不能再有其他参数（即只能是最后一个参数），否则会报错。

### 箭头函数

#### 基本用法

ES6 允许使用“箭头”（`=>`）定义函数。

```javascript
var f = v => v;

// 等同于
var f = function (v) {
  return v;
};
```

如果箭头函数不需要参数或需要多个参数，就使用一个**圆括号**代表参数部分。

```javascript
var f = () => 5;
// 等同于
var f = function () { return 5 };

var sum = (num1, num2) => num1 + num2;
// 等同于
var sum = function(num1, num2) {
  return num1 + num2;
};
```

如果箭头函数的代码块部分多于一条语句，就要使用大括号将它们括起来，并且使用`return`语句返回。

```javascript
var sum = (num1, num2) => { return num1 + num2; }
```

由于大括号被解释为代码块，所以如果箭头函数直接返回一个**对象**，必须在<u>对象外面加上括号</u>，否则会报错。

```javascript
// 报错
let getTempItem = id => { id: id, name: "Temp" };

// 不报错
let getTempItem = id => ({ id: id, name: "Temp" });
```

#### 使用注意点

箭头函数有几个使用**注意点**：

（1）箭头函数没有自己的`this`对象。

（2）不可以当作<u>构造函数</u>，也就是说，不可以对箭头函数使用`new`命令，否则会抛出一个错误。

（3）不可以使用`arguments`对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。

（4）不可以使用`yield`命令，因此箭头函数不能用作 Generator 函数。

上面四点中，第一点尤其值得注意。`this`对象的指向是可变的，但是在箭头函数中，它是固定（静态）的。

## 对象的扩展

### 属性的简洁表示法

ES6 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法。这样的书写更加简洁。

```javascript
const foo = 'bar';
const baz = {foo};
// 等同于
const baz = {foo: foo};
```

下面是另一个例子。

```javascript
function f(x, y) {
  return {x, y};
}
// 等同于
function f(x, y) {
  return {x: x, y: y};
}

f(1, 2) // Object {x: 1, y: 2}
```

除了属性简写，**方法**也可以简写。

```javascript
const o = {
  method() {
    return "Hello!";
  }
};
// 等同于
const o = {
  method: function() {
    return "Hello!";
  }
};
```

## 数组的扩展

### 数组的扩展

扩展运算符（spread）是三个点（`...`）。它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列。

```javascript
console.log(...[1, 2, 3])
// 1 2 3

console.log(1, ...[2, 3, 4], 5)
// 1 2 3 4 5

[...document.querySelectorAll('div')]
// [<div>, <div>, <div>]
```

## Symbol

### 概述

> ES6 引入了一种新的原始数据类型`Symbol`，表示独一无二的值。它是 JavaScript 语言的**第七种**数据类型。
>

Symbol 值通过`Symbol`函数生成。这就是说，<u>对象的属性名</u>现在可以有两种类型，一种是原来就有的字符串，另一种就是新增的 Symbol 类型。凡是属性名属于 Symbol 类型，就都是**独一无二**的，可以保证不会与其他属性名产生冲突。

```javascript
let s = Symbol();

typeof s
// "symbol"
```

上面代码中，变量`s`就是一个独一无二的值。`typeof`运算符的结果，表明变量`s`是 Symbol 数据类型，而不是字符串之类的其他类型。

- `Symbol`函数可以接受一个字符串作为参数，表示对 Symbol 实例的描述，主要是为了在控制台显示，或者转为字符串时，比较容易区分。

```javascript
let s1 = Symbol('foo');
let s2 = Symbol('bar');

s1 // Symbol(foo)
s2 // Symbol(bar)

s1.toString() // "Symbol(foo)"
s2.toString() // "Symbol(bar)"
```

> 注意，`Symbol`函数前不能使用`new`命令，否则会报错。
>

- Symbol 值不能与其他类型的值进行运算，会报错。

```javascript
let sym = Symbol('My symbol');

"your symbol is " + sym
// TypeError: can't convert symbol to string
`your symbol is ${sym}`
// TypeError: can't convert symbol to string
```

但是，Symbol 值可以显式转为字符串。

```javascript
let sym = Symbol('My symbol');

String(sym) // 'Symbol(My symbol)'
sym.toString() // 'Symbol(My symbol)'
```

- 注意，`Symbol`函数的参数只是表示对当前 Symbol 值的描述，因此相同参数的`Symbol`函数的返回值是不相等的。

```javascript
// 没有参数的情况
let s1 = Symbol();
let s2 = Symbol();

s1 === s2 // false

// 有参数的情况
let s1 = Symbol('foo');
let s2 = Symbol('foo');

s1 === s2 // false
```

### 作为属性名的 Symbol

由于每一个 Symbol 值都是不相等的，这意味着 Symbol 值可以作为标识符，用于对象的属性名，就能保证不会出现同名的属性。这对于一个对象由多个模块构成的情况非常有用，能防止某一个键被不小心改写或覆盖。

```javascript
let mySymbol = Symbol();

// 第一种写法
let a = {};
a[mySymbol] = 'Hello!';

// 第二种写法
let a = {
  [mySymbol]: 'Hello!'
};

// 以上写法都得到同样结果
a[mySymbol] // "Hello!"
```

> 注意，Symbol 值作为对象属性名时，不能用点运算符。
>

```javascript
const mySymbol = Symbol();
const a = {};

a.mySymbol = 'Hello!';
a[mySymbol] // undefined
a['mySymbol'] // "Hello!"
```

上面代码中，因为点运算符后面总是字符串，所以不会读取`mySymbol`作为标识名所指代的那个值，导致`a`的属性名实际上是一个字符串，而不是一个 Symbol 值。

### Symbol.for()

有时，我们希望重新使用同一个 Symbol 值，`Symbol.for()`方法可以做到这一点。

它接受一个字符串作为参数，然后**搜索**有没有以该参数作为名称的 Symbol 值。如果有，就返回这个 Symbol 值，否则就新建一个以该字符串为名称的 Symbol 值，并将其注册到全局。

```javascript
let s1 = Symbol.for('foo');
let s2 = Symbol.for('foo');

s1 === s2 // true
```

上面代码中，`s1`和`s2`都是 Symbol 值，但是它们都是由同样参数的`Symbol.for`方法生成的，所以实际上是同一个值。

## Iterator

### Iterator（遍历器）的概念

遍历器（Iterator）是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署 Iterator 接口，就可以完成**遍历**操作（即依次处理该数据结构的所有成员）。

Iterator 的**作用**有三个：一是为各种数据结构，提供一个统一的、简便的访问接口；二是使得数据结构的成员能够按某种次序排列；三是 ES6 创造了一种新的遍历命令`for...of`循环，Iterator 接口主要供`for...of`消费。

------

**Iterator 的遍历过程**：

（1）创建一个指针对象，指向当前数据结构的起始位置。也就是说，遍历器对象本质上，就是一个指针对象。

（2）第一次调用指针对象的`next`方法，可以将指针指向数据结构的第一个成员。

（3）第二次调用指针对象的`next`方法，指针就指向数据结构的第二个成员。

（4）不断调用指针对象的`next`方法，直到它指向数据结构的结束位置。

> 原生具备 Iterator 接口的数据结构如下。
>
> - Array
> - Map
> - Set
> - String
> - TypedArray
> - 函数的 arguments 对象
> - NodeList 对象

下面的例子是数组的`Symbol.iterator`属性。

```javascript
let arr = ['a', 'b', 'c'];
let iter = arr[Symbol.iterator]();

iter.next() // { value: 'a', done: false }
iter.next() // { value: 'b', done: false }
iter.next() // { value: 'c', done: false }
iter.next() // { value: undefined, done: true }
```

上面代码中，变量`arr`是一个数组，原生就具有遍历器接口，部署在`arr`的`Symbol.iterator`属性上面。所以，调用这个属性，就得到遍历器对象。

### for...of 循环

数组原生具备`iterator`接口（即默认部署了`Symbol.iterator`属性），`for...of`循环本质上就是调用这个接口产生的遍历器，可以用下面的代码证明。

```javascript
const arr = ['red', 'green', 'blue'];

for(let v of arr) {
  console.log(v); // red green blue
}
```

## Generator 函数的语法

Generator 函数是 ES6 提供的一种**异步**编程解决方案，语法行为与传统函数完全不同。

形式上，Generator 函数是一个普通函数，但是有两个特征。一是，`function`关键字与函数名之间有一个星号；二是，函数体内部使用`yield`表达式，定义不同的内部状态（`yield`在英语里的意思就是“产出”）。

```javascript
function* helloWorldGenerator() {
  yield 'hello';
  yield 'world';
  return 'ending';
}

var hw = helloWorldGenerator();
```

上面代码定义了一个 Generator 函数`helloWorldGenerator`，它内部有两个`yield`表达式（`hello`和`world`），即该函数有三个状态：hello，world 和 return 语句（结束执行）。

## Promise 对象

### Promise 的理解和使用

#### 理解

- 抽象表达:  

1) Promise 是一门新的技术(ES6 规范) 

2) Promise 是 JS 中进行异步编程的新解决方案 

备注：旧方案是单纯使用回调函数 

- 具体表达: 

1) 从语法上来说: Promise 是一个构造函数 

2) 从功能上来说: promise 对象用来封装一个异步操作并可以获取其成功/ 失败的结果值

#### 状态改变

- `pending` 变为 `resolved`
- `pending` 变为 `rejected` 

> 说明: 只有这 2 种, 且一个 promise 对象只能改变一次
>
> 无论变为成功还是失败, 都会有一个结果数据

#### Promise对象的值

实例对象的一个属性【`PromiseResult`】，保存着对象【成功/失败】的结果。即`resolve`/`reject`里的实参。

#### Promise的基本流程

<img src="https://img.zjgsuzjx.top/img/images/2021/07/16/cbb49128d7f31e316acc77c46c7952d7.jpg" alt="cbb49128d7f31e316acc77c46c7952d7.jpg" border="0" />

#### 基本使用

##### # 基本编码流程

```js
function rand(){
    return Math.random()*100
}
const p = new Promise((resolve,reject)=>{
    setTimeout(() => {
        let n=rand() // 得到一个随机数
        if(n<=30){
            resolve(n); // 将Promise状态设置为成功
        }else{
            reject(n); // 将Promise状态设置为失败
        }
    }, 1000);
})
// 调用then方法
p.then((value)=>{
    alert('congralution')
},(reason)=>{
    alert('failed')
})
```

成功则调用then的第一个回调函数，失败则调用第二个回调函数。

##### # 用promise封装文件读取

```js
const fs=require('fs')
let p=new Promise((resolve, reject) => {
    fs.readFile('./demo.txt',(err, data) => {
        if(err) reject(err)
        resolve(data)
    })
})
p.then(value => {
    console.log(value.toString())
},reason => {
    console.log(reason.toString())
})
```

##### # 用promise封装AJAX请求

```js
function sendAJAX(url){
    // 返回一个Promise对象
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest()
        xhr.open('get', 'url')
        xhr.send();
        xhr.onreadystatechange = function () {
            if (xhr.readyState == 4) {
                if (xhr.status == 200) {
                    resolve(xhr.responseText)
                } else {
                    reject(xhr.status)
                }
            }
        }
    })
}

sendAJAX('url').then(value => {
    console.log(value)
}, reason => {
    console.warn(reason)
})
```

##### # 借助Node内置方法进行文件读取

```js
const util=require('util')
const fs=require('fs')
// 返回一个Promise类型的函数
let mineReadFile=util.promisify(fs.readFile)

mineReadFile('./demo.txt').then(value => {
    console.log(value.toString())
})
```

### Promise的使用

#### API

##### # Promise 构造函数: `Promise (excutor) {}`

(1) executor 函数: 执行器 `(resolve, reject) => {}`  

(2) resolve 函数: 内部定义成功时我们调用的函数 `value => {}` 

(3) reject 函数: 内部定义失败时我们调用的函数 `reason => {}` 

> **说明**: `executor` 会在 Promise 内部立即**同步调用**,异步操作在执行器中执行

##### # catch 方法: `(onRejected) => {}`

onRejected 函数: 失败的回调函数 `(reason) => {}`

> **说明**: then()的语法糖, 相当于: `then(undefined, onRejected)`

##### # resolve 方法: `(value) => {}`

`value`: 成功的数据或 promise 对象

```js
let p1=Promise.resolve(200)
/*
* 如果插入的参数为非 Promise类型的对象，则返回的结果为成功promise对象
* 如果插入的参数为 Promise 对象，则参数的结果决定了resolve的结果
* */
let p2=Promise.resolve(new Promise((resolve, reject) => {
    // resolve('OK')
    reject('error')
}))
// 当结果为失败时
p2.catch(reason => {
    console.log(reason)
})
```

> **说明**: 返回一个成功/失败的 promise 对象

##### # reject 方法: `(reason) => {}`

`reason`: 失败的原因 

> **说明**: 返回一个失败的 promise 对象

##### # all 方法: `(promises) => {}`

`promises`: 包含 n 个 promise 的数组

```js
let p1=new Promise((resolve, reject) => {
    resolve('OK')
})
let p2=Promise.resolve('success')
let p3=Promise.resolve('yeah')
// 只要一个是失败，则返回失败的Promise
const result=Promise.all([p1,p2,p3])
// 若都是成功，返回结果为成功结果组成的数组；若为失败，则为失败的值
console.log(result)
```

> **说明**: 返回一个新的 promise, 只有所有的 promise 都成功才成功, 只要有一个失败了就 直接失败

##### # race 方法: `(promises) => {}`

`promises`: 包含 n 个 promise 的数组

> **说明**: 返回一个新的 promise, 第一个完成的 promise 的结果状态就是最终的结果状态

```js
let p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('OK')
    }, 1000)
})
let p2 = Promise.resolve('success')
let p3 = Promise.resolve('yeah')

const result = Promise.race([p1, p2, p3])
// 返回p2
console.log(result)
```

#### promise 的关键问题

##### # 如何改变 promise 的状态

(1) resolve(value): 如果当前是 pending 就会变为 resolved 

(2) reject(reason): 如果当前是 pending 就会变为 rejected 

(3) 抛出异常: 如果当前是 pending 就会变为 rejected

```js
let p=new Promise((resolve, reject) => {
    resolve('ok') // pending => fulfilled(resolved)
    reject('error') // pending => rejected
    throw '出问题了'
})
```

> - 一个 promise 指定多个成功/失败回调函数, 都会调用吗?
>
> 当 promise 改变为对应状态时**都会**调用

##### # 状态和回调函数先后问题

正常情况下是先指定回调再改变状态, 但也可以先改状态再指定回调。

- 如何先改状态再指定回调?

① 在执行器中直接调用 resolve()/reject()

② 延迟更长时间才调用 then()

- 什么时候才能得到数据?

① 如果先指定的回调, 那当状态发生改变时, 回调函数就会调用, 得到数据

② 如果先改变的状态, 那当指定回调时, 回调函数就会调用, 得到数据

> **总结**：Promise支持同步和异步，回调函数最终都会等Promise状态发生改变再执行。

##### # Promise.then的返回状态

**简单表达**: 新 promise 的结果状态由由 `then()`指定的回调函数执行的结果决定

**详细表达**: 

① 如果抛出异常, 新 promise 变为 `rejected`, `reason` 为抛出的异常 

② 如果返回的是非 promise 的任意值, 新 promise 变为 `resolved`, `value` 为返回的值 

③ 如果返回的是另一个新 promise, 此 promise 的结果就会成为新 promise 的结果

```js
let p=new Promise((resolve, reject) => {
    resolve('ok')
})
let result=p.then(value => {
    // console.log(value);
    // 1.抛出错误
    // throw 'problem'
    // 2. 返回结果是非 Promise类型的对象
    // return 521
    // 3. 返回结果是Promise对象
    return new Promise((resolve, reject) => {
        reject('error')
    })
})
console.log(result)
```

##### # Promise串连多个操作任务

(1) promise 的 `then()`返回一个新的 promise, 可以开成 `then()`的链式调用

(2) 通过 `then` 的链式调用串连多个同步/异步任务

```js
let p=new Promise((resolve, reject) => {
    setTimeout(()=>{
        resolve('ok')
    },1000)
})
p.then(value => {
    // 返回一个Promise对象
    return new Promise((resolve, reject) => {
        resolve('success')
    })
}).then(value => {
    console.log(value) // success
}).then(value => {
    console.log(value) // undefined，因为上一个then的结果是成功，但是没有返回值return
})
```

##### # Promise 异常传透

(1) 当使用 promise 的 `then` 链式调用时, 可以在最后指定失败的回调

(2) 前面任何操作出了**异常**, 都会传到**最后失败**的回调中处理

```js
let p=new Promise((resolve, reject) => {
    setTimeout(()=>{
        resolve('ok')
    },1000)
})
p.then(value => {
    console.log(111) // 会执行
}).then(value => {
    throw 'problem'
}).then(value => {
    console.log(333) // 不会执行
}).catch(reason => {
    console.warn(reason) // problem
})
```

> 简单来讲，就是在最后部分来处理前面遇到的错误。

##### # 中断Promise链

(1) 当使用 promise 的 `then` 链式调用时, 在中间中断, 不再调用后面的回调函数

(2) **办法**: 在回调函数中返回一个 pendding 状态的 promise 对象

```js
let p = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('ok')
    }, 1000)
})
p.then(value => {
    console.log(111)
    // 返回一个pending状态的Promise对象
    return new Promise(() => {})
}).then(value => {
    console.log(222) // 不会执行
}).then(value => {
    console.log(333) // 会执行
}).catch(reason => {
    console.warn(reason)
})
```

### async 与 await

#### mdn 文档

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/async_function

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/await

#### async 函数

函数的返回值为 `promise` 对象

promise 对象的结果由 `async` 函数执行的**返回值**决定

```js
async function main() {
    // 状态是成功，值是返回值521
    return 521
    // 状态跟随返回的Promise状态，值是resolve或reject
    return new Promise((resolve, reject) => {
        resolve('ok')
    })
    // 状态是失败，值是返回值no
    throw "no"
}
let result=main()
console.log(result)
```

> 跟then结果处理是完全一致的

#### await 表达式

`await` 必须写在 `async` 函数中, 但 `async` 函数中可以没有 `await`

> **注意**：如果 `await` 的 `promise` 失败了, 就会抛出异常, 需要通过 `try...catch` 捕获处理

```js
async function main() {
    let p1=new Promise((resolve, reject) => {
        resolve('ok')
    })
    let p2=new Promise((resolve, reject) => {
        reject('error')
    })
    // 如果表达式是 promise 对象, await 返回的是 promise 成功的值
    let res1=await p1
    // 如果表达式是其它值, 直接将此值作为 await 的返回值
    let res2=await 20; // 很少见
    // 如果Promise是失败的状态
    let res3=await p2
    console.log(res1) // ok
    console.log(res2) // 20
    try{
        console.log(res3)
    }catch (e) {
        console.log(e)
    }
}
main()
```

#### async和await结合实践

实现：读取三个文件内容，并进行拼接。

```js
const fs = require('fs');
const util = require('util');
const mineReadFile = util.promisify(fs.readFile);

//回调函数的方式
// fs.readFile('./resource/1.html', (err, data1) => {
//     if(err) throw err;
//     fs.readFile('./resource/2.html', (err, data2) => {
//         if(err) throw err;
//         fs.readFile('./resource/3.html', (err, data3) => {
//             if(err) throw err;
//             console.log(data1 + data2 + data3);
//         });
//     });
// });

//async 与 await
async function main(){
    try{
        //读取第一个文件的内容
        let data1 = await mineReadFile('./resource/1.html');
        let data2 = await mineReadFile('./resource/2.html');
        let data3 = await mineReadFile('./resource/3.html');
        console.log(data1 + data2 + data3);
    }catch(e){
        console.log(e.code);
    }
}
main();
```



















